---
title: コンパイラ エラー C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: 3f32307e519394433927d49aa92333fdff7b70f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378870"
---
# <a name="compiler-error-c2883"></a>コンパイラ エラー C2883

'name': 'identifier' を使用して宣言によって導入されると競合して関数の宣言

関数を複数回定義しようとしました。 最初の定義が、名前空間から行われた、`using`宣言します。 2 つ目は、ローカルの定義をしました。

次の例では、C2883 が生成されます。

```
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```