---
title: _mm_cvttss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: cfdea6ded622cbcbe42bd555edb3029fabad7823
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023712"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x

**Microsoft 固有の仕様**

出力拡張 x64 バージョンの 64 ビットの整数に切り捨て単精度浮動小数点数に変換 (`cvttss2si`) 命令。

## <a name="syntax"></a>構文

```
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

#### <a name="parameters"></a>パラメーター

*value*<br/>
[in]`__m128`単精度浮動小数点値を含む構造体。

## <a name="return-value"></a>戻り値

最初の浮動小数点値の 64 ビット整数への変換の結果。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

組み込みの異なる`_mm_cvtss_si64x`不正確な変換は、ゼロに向かって切り捨てられます。 その内のみです。 `__m128`構造体が、XMM レジスタを表す、生成された命令をシステム メモリに、XMM レジスタからデータを移動します。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__m128](../cpp/m128.md)<br/>
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)