---
title: iterator 構造体
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 1dd62a6141e690d3bd4dcad69aa107c126a0f386
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224104"
---
# <a name="iterator-struct"></a>iterator 構造体

ユーザー定義の iterator クラスが適切に動作することを確認するために使用する空の基底構造体`iterator_trait`秒。

## <a name="syntax"></a>構文

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Remarks

このテンプレート構造体は、すべての反復子の基本データ型として機能します。 これは、メンバーの型を定義します。

- `iterator_category` (テンプレート パラメーター `Category` のシノニム)。

- `value_type` (テンプレート パラメーター `Type` のシノニム)。

- `difference_type` (テンプレート パラメーター `Distance` のシノニム)。

- `distance_type` (テンプレート パラメーター `Distance` のシノニム)。

- `pointer` (テンプレート パラメーター `Pointer` のシノニム)。

- `reference` (テンプレート パラメーター `Reference` のシノニム)。

なお`value_type`定数型の場合でもをすることはできません`pointer`のオブジェクトを指して**const** `Type`参照のオブジェクトを指定して**const** `Type`します。

## <a name="example"></a>例

反復子の基底クラスの型の宣言方法や使用例については、「[iterator_traits](../standard-library/iterator-traits-struct.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<iterator>

**名前空間:** std

## <a name="see-also"></a>関連項目

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)<br/>
