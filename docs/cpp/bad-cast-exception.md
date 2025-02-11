---
title: bad_cast 例外
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 7384394fb53c6aa4bc009a903ba0ed22bf0ed0d6
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998774"
---
# <a name="bad_cast-exception"></a>bad_cast 例外

参照型へのキャストが失敗した結果として、 **bad_cast**例外が**dynamic_cast**演算子によってスローされます。

## <a name="syntax"></a>構文

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>コメント

**Bad_cast**のインターフェイスは次のとおりです。

```cpp
class bad_cast : public exception
```

次のコードには、 **bad_cast**例外をスローする失敗した**dynamic_cast**の例が含まれています。

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

この例外がスローされるのは、キャストされているオブジェクト (図形) が指定されたキャスト型 (Circle) から派生していないためです。 例外を回避するには、`main` に次の宣言を追加します。

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

次に、 **try**ブロック内のキャストの意味を次のように逆にします。

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 型のオブジェクトのコンストラクター。|

### <a name="functions"></a>関数

|関数|説明|
|-|-|
|[結果](#what)|TBD|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|1つの @no__t 0 オブジェクトを別のオブジェクトに代入する代入演算子。|

## <a name="bad_cast"></a>bad_cast

`bad_cast` 型のオブジェクトのコンストラクター。

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>operator =

1つの @no__t 0 オブジェクトを別のオブジェクトに代入する代入演算子。

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>結果

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>関連項目

[Dynamic_cast 演算子](../cpp/dynamic-cast-operator.md)\
[キーワード](../cpp/keywords-cpp.md)\
[C++ 例外処理](../cpp/cpp-exception-handling.md)
