---
title: add_rvalue_reference クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: e5e658f16657c0021b78175e87d122a3accd11eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411175"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference クラス

テンプレート パラメーターがオブジェクトまたは関数の型の場合に、その右辺値参照型を作成します。 それ以外の場合、参照縮小のセマンティクスのため、型はテンプレート パラメーターと同じです。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
変更する型。

## <a name="remarks"></a>Remarks

`add_rvalue_reference`クラスという名前のメンバーには`type`、右辺値参照をテンプレート パラメーターの型のエイリアスである*T*します。非オブジェクトおよび関数ではない型の参照縮小のセマンティクスを意味する、 *T*、`T&&`は、 *T*します。たとえば、 *T*が左辺値参照型では、`add_rvalue_reference<T>::type`が左辺値参照型で、右辺値参照ではありません。

便宜上、 \<type_traits > ヘルパー テンプレートを定義します`add_rvalue_reference_t`、そのエイリアス、`type`のメンバー`add_rvalue_reference`します。

## <a name="example"></a>例

このコード例では、static_assert を使用して、右辺値参照型を `add_rvalue_reference` と`add_rvalue_reference_t` を使用して作成する方法、および左辺値参照型での `add_rvalue_reference` の結果を右辺値参照ではなく左辺値参照型に縮小する方法を示します。

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>必要条件

ヘッダー: \<type_traits >

Namespace: std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference クラス](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference クラス](../standard-library/is-rvalue-reference-class.md)<br/>
