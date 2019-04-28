---
title: _mm_stream_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 76c6c848351df773b9857b2f83726b64db982d9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263231"
---
# <a name="mmstreamss"></a>_mm_stream_ss

**Microsoft 固有の仕様**

メモリ位置に、キャッシュを汚染することがなく 32 ビットのデータを書き込みます。

## <a name="syntax"></a>構文

```
void _mm_stream_ss(
   float * Dest,
   __m128 Source
);
```

#### <a name="parameters"></a>パラメーター

*追加先*<br/>
[out]ソース データが書き込まれる場所へのポインター。

*ソース*<br/>
[in]128 ビットの数値を含む、`float`値を 32 ビットの下で記述する.

## <a name="return-value"></a>戻り値

なし。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>コメント

この組み込み関数は`movntss`命令を生成します。 この命令のハードウェアのサポートを確認するのには、呼び出し、`__cpuid`で組み込み`InfoType=0x80000001`のビット 6 をチェックおよび`CPUInfo[2] (ECX)`します。 このビットは、それ以外の場合、命令がサポートされている場合は 1 と 0 です。

使用するコードを実行する場合、`_mm_stream_ss`がサポートされていないハードウェアに組み込み、`movntss`命令の場合、結果は予測できません。

## <a name="example"></a>例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**Microsoft 固有の仕様はここまで**

高度なマイクロ デバイス, inc. copyright 2007All rights reserved. 高度なマイクロ デバイス, Inc. からのアクセス許可を持つ再現

## <a name="see-also"></a>関連項目

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)<br/>
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)<br/>
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)