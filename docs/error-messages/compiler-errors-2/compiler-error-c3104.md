---
title: コンパイラ エラー C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: fee023809246634f2f3da266a718e45861eae76e
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447833"
---
# <a name="compiler-error-c3104"></a>コンパイラ エラー C3104

無効な属性引数

属性に無効な引数を指定したとします。

参照してください[属性パラメーターの型](../../extensions/attribute-parameter-types-cpp-component-extensions.md)詳細についてはします。

このエラーは、Visual Studio 2005 で行ったコンパイラ準拠作業の結果として生成されることができます: 集約の初期化リストから配列の型が推測不要になったときに、カスタム属性には、マネージ配列を渡すことです。 これで、コンパイラでは初期化子リストと同様に、配列の型を指定することが必要です。

## <a name="example"></a>例

次の例では、C3104 が生成されます。

```
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>例

次の例では、C3104 が生成されます。

```
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
