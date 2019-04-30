---
title: is_member_function_pointer クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_function_pointer
helpviewer_keywords:
- is_member_function_pointer class
- is_member_function_pointer
ms.assetid: 02e372c4-2714-40f2-b376-2e10ca91c8ed
ms.openlocfilehash: 0eb758977abf889a7d5ec8cdec9213980493ba2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351931"
---
# <a name="ismemberfunctionpointer-class"></a>is_member_function_pointer クラス

型がメンバー関数へのポインターであるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_member_function_pointer;
```

### <a name="parameters"></a>パラメーター

*Ty*<br/>
照会する型。

## <a name="remarks"></a>Remarks

場合、型述語のインスタンスは true を保持型*Ty*メンバー関数へのポインターまたは`cv-qualified`メンバー関数は、それ以外の場合は false を保持するポインター。

## <a name="example"></a>例

```cpp
// std__type_traits__is_member_function_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_function_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_function_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_function_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_function_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_function_pointer<trivial *> == false
is_member_function_pointer<int trivial::*> == false
is_member_function_pointer<int (functional::*)()> == true
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer クラス](../standard-library/is-member-pointer-class.md)<br/>
