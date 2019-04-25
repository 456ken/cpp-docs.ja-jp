---
title: __min
ms.date: 04/05/2018
apiname:
- __min
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
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: f9e867cd1f3e3519e440c91895e61e317d9688a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156552"
---
# <a name="min"></a>__min

プリプロセッサ マクロには、2 つの値のうち、小さい方を返します。

## <a name="syntax"></a>構文

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>パラメーター

*a*、 *b*<br/>
いずれかの値の型を**<** 演算子で動作します。

## <a name="return-value"></a>戻り値

2 つの引数のうちの小さい方。

## <a name="remarks"></a>Remarks

**_ _Min**マクロは、2 つの値を比較し、小規模な 1 つの値を返します。 引数には、符号付きまたは符号なしのすべての数値データ型を指定できます。 引数と戻り値はともに同じデータ型である必要があります。

返される引数は、マクロで 2 回評価されます。 これにより、予期しない結果がそれを評価するときなど、その値を変更する式の引数の場合`*p++`します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>例

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
