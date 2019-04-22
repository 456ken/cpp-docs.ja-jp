---
title: __umulh
ms.date: 11/04/2016
f1_keywords:
- __umulh
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
ms.openlocfilehash: 3a42de276b483f98e2eaf9d0c8505d7f1d5b5bca
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026566"
---
# <a name="umulh"></a>__umulh

**Microsoft 固有の仕様**

2 つの 64 ビット符号なし整数の積の上位 64 ビットを返します。

## <a name="syntax"></a>構文

```
unsigned __int64 __umulh(
   unsigned __int64 a,
   unsigned __int64 b
);
```

#### <a name="parameters"></a>パラメーター

*a*<br/>
[in]乗算する最初の数値。

*b*<br/>
[in]乗算する 2 番目の数値。

## <a name="return-value"></a>戻り値

乗算で得られる 128 ビットの結果の上位 64 ビット。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__umulh`|X64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```
// umulh.cpp
// processor: X64
#include <cstdio>
#include <intrin.h>

int main()
{
    unsigned __int64 i = 0x10;
    unsigned __int64 j = 0xFEDCBA9876543210;
    unsigned __int64 k = i * j; // k has the low 64 bits
                                // of the product.
    unsigned __int64 result;
    result = __umulh(i, j); // result has the high 64 bits
                            // of the product.
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);
    return 0;
}
```

```Output
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)