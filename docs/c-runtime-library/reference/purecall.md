---
title: _purecall
ms.date: 11/04/2016
apiname:
- _purecall
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: df6dde91ccb952e66eb77c841b2b1ace12756b8c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446628"
---
# <a name="purecall"></a>_purecall

純粋仮想関数が呼び出された場合の、既定のエラー ハンドラーです。 純粋仮想メンバー関数が呼び出されると、コンパイラによってこの関数を呼び出すコードが生成されます。

## <a name="syntax"></a>構文

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Remarks

**_Purecall**関数は、Microsoft の Microsoft 固有の実装詳細C++コンパイラ。 この関数はコードで直接呼び出されるものではなく、パブリック ヘッダー宣言がありません。 C ランタイム ライブラリのパブリック エクスポートであるため、ここで説明しています。

純粋仮想関数には実装がないため、この関数への呼び出しはエラーになります。 コンパイラを呼び出すコードを生成、 **_purecall**純粋仮想関数が呼び出されると、エラー ハンドラー関数。 既定では、 **_purecall**プログラムを終了します。 を終了する前に、 **_purecall**関数によって呼び出されます、 **_purecall_handler**プロセスのいずれかが設定されている場合に機能します。 純粋仮想関数の呼び出し用に独自のエラー ハンドラー関数をインストールして呼び出しをキャッチし、デバッグまたはレポート作成に使用することができます。 エラー ハンドラーを使用するを持つ関数を作成、 **_purecall_handler**のシグネチャを使用して[_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)を現在のハンドラーします。

## <a name="requirements"></a>必要条件

**_Purecall**関数にはヘッダー宣言がありません。 **_Purecall_handler**で定義されている typedef \<stdlib.h >。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
