---
title: ソフトウェア例外の発生
ms.date: 11/04/2016
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
ms.openlocfilehash: 49ee800bafff017c29b73c5f6fd64318009a140a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403465"
---
# <a name="raising-software-exceptions"></a>ソフトウェア例外の発生

プログラム エラーの最も一般的な原因のいくつかは、システムによって例外としてフラグが設定されません。 たとえば、メモリ ブロックを割り当てるときにメモリが不足していると、ランタイム関数または API 関数で例外は発生しませんが、エラー コードが返されます。

ただし、扱うことができますいずれかの条件を例外として、コードでその状態を検出して呼び出すことによって、報告、 [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552)関数。 この方法でエラーにフラグを設定すれば、構造化例外処理の長所をあらゆるランタイム エラーに取り込むことができます。

エラーで構造化例外処理を使用するには、次の手順に従います。

- イベントごとに例外コードを定義します。

- 呼び出す`RaiseException`問題を検出した場合。

- 例外処理フィルターを使用して、定義した例外コードをテストします。

\<Winerror.h > ファイルは例外コードの形式を示しています。 既存の例外コードと競合するコードを定義しないように、第 3 上位ビットを 1 に設定します。 4 つの最上位ビットは、次の表に示すように設定する必要があります。

|ビット|推奨バイナリ設定|説明|
|----------|--------------------------------|-----------------|
|31-30|11|これら 2 つのビットには、コードの基本的なステータスがについて説明します。11 = エラー、00 = 成功、01 = 情報、10 = 警告します。|
|29|1|クライアント ビット。 ユーザー定義コードの場合は 1 に設定します。|
|28|0|予約済みのビット  (0 に設定しておきます)。|

必要であれば、最初の 2 ビットをバイナリ 11 以外に設定できますが、通常はほとんどの例外に "エラー" を設定します。 注意すべき重要事項は、前の表に示すようにビット 29 と 28 を設定することです。

結果のエラー コードが最上位 4 ビットを 16 進数の E に設定したがって必要たとえば、次の定義は、任意の Windows 例外コードと競合しない例外コードを定義します。 (ただし、サード パーティの DLL がどのコードを使用するか確認する必要があります)。

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

例外コードを定義したら、そのコードを使用して例外を発生させることができます。 たとえば、次のコード生成、`STATUS_INSUFFICIENT_MEM`メモリ割り当ての問題への応答での例外。

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

例外を簡単に発生させるには、最後の 3 つのパラメーターを 0 に設定します。 最後の 3 つのパラメーターは、追加情報を渡し、ハンドラーの実行を中止するフラグを設定するときに使用します。 参照してください、 [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552)詳細については、Windows SDK 内の関数。

例外処理フィルターで、定義したコードをテストできます。 例:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>関連項目

[例外ハンドラーの記述](../cpp/writing-an-exception-handler.md)<br/>
[構造化例外処理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)