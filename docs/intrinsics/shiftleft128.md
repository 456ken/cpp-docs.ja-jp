---
title: __shiftleft128
ms.date: 11/04/2016
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5fcb797694c7a45dc4f2113f3d2ed4a2f578c894
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390413"
---
# <a name="shiftleft128"></a>__shiftleft128

**Microsoft 固有の仕様**

64 ビットの 2 つの数 `LowPart` および `HighPart` で表される 128 ビットの数を、`Shift` で指定されたビット数だけ左にシフトし、結果の上位 64 ビットを返します。

## <a name="syntax"></a>構文

```
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>パラメーター

*下位*<br/>
[in]シフトする 128 ビット数の下位 64 ビット。

*HighPart*<br/>
[in]シフトする 128 ビット数の上位 64 ビット。

*Shift*<br/>
[in]シフトするビット数。

## <a name="return-value"></a>戻り値

結果の上位 64 ビット。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__shiftleft128`|X64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

`Shift` の値は常にモジュロ 64 です。このため、たとえば `__shiftleft128(1, 0, 64)` をコールすると、上位部分が `0` ビット右にシフトされ、下位部分である `0` が返されます。`1` ではありません。

## <a name="example"></a>例

```
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__shiftright128](../intrinsics/shiftright128.md)<br/>
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)