---
title: コンパイラ エラー C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 8a9ec2f59f362df284e9bd5cd8df6ae986d59d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266271"
---
# <a name="compiler-error-c2682"></a>コンパイラ エラー C2682

'type1' から 'type2' に変換する casting_operator を使用することはできません。

キャスト演算子と互換性のない型を変換しようとしました。 たとえば、使用することはできません、 [dynamic_cast](../../cpp/dynamic-cast-operator.md)参照へのポインターに変換する演算子。 `dynamic_cast`演算子はキャスト修飾子を使用できることはできません。 型のすべての修飾子が一致する必要があります。

使用することができます、`const_cast`などの属性を削除するオペレーター `const`、 `volatile`、または`__unaligned`します。

次の例では、C2682 が生成されます。

```
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

次の例では、C2682 が生成されます。

```
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```