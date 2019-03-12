---
title: _setjmp3
ms.date: 11/04/2016
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: e2c89acf1de88b831d70a0f438cdf14148a48632
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741808"
---
# <a name="setjmp3"></a>_setjmp3

内部 CRT 関数。 `setjmp` 関数の新しい実装。

## <a name="syntax"></a>構文

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>パラメーター

*env*<br/>
[out] 状態情報を格納するためのバッファーのアドレス。

*count*<br/>
[in] `optional parameters` に格納されている情報の追加 `DWORD` の数。

*省略可能なパラメーター*<br/>
[in] `setjmp` の組み込みによってプッシュダウンされる追加データ。 最初の `DWORD` は、追加データをアンワインドして不揮発性レジスタの状態に戻るために使用される関数ポインターです。 2 番目の `DWORD` は、復元される試行レベルです。 これ以上のデータは、`jmp_buf` の一般的なデータ配列に保存されます。

## <a name="return-value"></a>戻り値

常に 0 を返します。

## <a name="remarks"></a>解説

この関数は C++ プログラムでは使用しないでください。 これは、C++ をサポートしない組み込み関数です。 `setjmp` の使用方法の詳細については、「[setjmp/longjmp の使用](../cpp/using-setjmp-longjmp.md)」をご覧ください。

## <a name="requirements"></a>要件

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)
