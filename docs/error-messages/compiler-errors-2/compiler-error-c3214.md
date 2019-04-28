---
title: コンパイラ エラー C3214
ms.date: 11/04/2016
f1_keywords:
- C3214
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
ms.openlocfilehash: e4f271ec4abdc05b5cf148e40a752b4d62cc884c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182549"
---
# <a name="compiler-error-c3214"></a>コンパイラ エラー C3214

'type': ジェネリック 'generic_type' のジェネリック パラメーター 'param' の型引数が無効です。制約 'constraint' を満たしていません

ジェネリック クラスの制約を満たしていないジェネリック クラスをインスタンス化するために型を指定しました。

次の例では C3214 が生成されます。

```
// C3214.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A
ref class C {};

ref class X : public A {};

int main() {
   C<int>^ c = new C<int>;   // C3214
   C<X ^> ^ c2 = new C<X^>;   // OK
}
```