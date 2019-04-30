---
title: is_base_of クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: 345301b5eeed7b66f18a54e56b9bee6346078634
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383673"
---
# <a name="isbaseof-class"></a>is_base_of クラス

一方の型がもう一方の型の基底クラスであるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>パラメーター

*ベース*<br/>
テスト対象の基底クラス。

*派生*<br/>
テスト対象の派生型。

## <a name="remarks"></a>Remarks

場合、型述語のインスタンスは true を保持型*基本*型の基本クラスは、*派生*、それ以外の場合は false を保持します。

## <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_convertible クラス](../standard-library/is-convertible-class.md)<br/>
