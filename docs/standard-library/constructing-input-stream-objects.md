---
title: 入力ストリーム オブジェクトのコンストラクト
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: 89d681f1a092957bc966d2ec788a0f9aa2261ada
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211989"
---
# <a name="constructing-input-stream-objects"></a>入力ストリーム オブジェクトのコンストラクト

`cin` オブジェクトのみを使う場合は、入力ストリームをコンストラクトする必要はありません。 次のものを使う場合は、入力ストリームをコンストラクトする必要があります。

- [入力ファイル ストリーム コンストラクター](#vclrfinputfilestreamconstructorsanchor8)

- [入力文字列ストリーム コンストラクター](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a> 入力ファイル ストリーム コンストラクター

入力ファイル ストリームは、2 つの方法で作成できます。

- 使用して、 **void**引数コンス トラクターを呼び出して、`open`メンバー関数。

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- コンストラクターの呼び出しでファイル名とモード フラグを指定し、それによってコンストラクション プロセスの間にファイルを開きます。

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="vclrfinputstringstreamconstructorsanchor9"></a> 入力文字列ストリーム コンストラクター

入力文字列ストリーム コンストラクターには、事前に割り当てられて初期化された記憶域のアドレスが必要です。

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>関連項目

[入力ストリーム](../standard-library/input-streams.md)<br/>
