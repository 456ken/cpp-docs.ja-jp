---
title: vector&lt;bool&gt;::reference クラス
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 7930c1cd93cd05a752d4997b9480c766ee26bd99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407719"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference クラス

`vector<bool>::reference` クラスは `bool&` をシミュレートするために [vector\<bool> クラス](../standard-library/vector-bool-class.md)によって提供されるプロキシ クラスです。

## <a name="remarks"></a>Remarks

C++ では、ネイティブにビットを直接参照しないため、シミュレートされた参照が必要です。 `vector<bool>` は、要素ごとに 1 ビットだけ使用します。このビットは、このプロキシ クラスを使用して参照できます。 ただし、参照のシミュレーションは、特定の代入が有効でないため、完全ではありません。 たとえば、ためのアドレス、`vector<bool>::reference`オブジェクトを作成できなかった、使用しようとする次のコード`vector<bool>::operator&`が正しくありません。

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|vector 要素のブール値を反転します。|
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|暗黙的な変換`vector<bool>::reference`に**bool**します。|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|ブール値をビットに割り当てます。または参照先の要素が保持している値をビットに割り当てます。|

## <a name="requirements"></a>必要条件

**ヘッダー**: \<vector>

**名前空間:** std

## <a name="see-also"></a>関連項目

[\<vector>](../standard-library/vector.md)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)<br/>
