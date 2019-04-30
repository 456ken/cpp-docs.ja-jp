---
title: コンパイラ エラー C2387
ms.date: 11/04/2016
f1_keywords:
- C2387
helpviewer_keywords:
- C2387
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
ms.openlocfilehash: df9e92bfa333be88e860bbdecd5acaa64ec80440
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393676"
---
# <a name="compiler-error-c2387"></a>コンパイラ エラー C2387

'type': あいまいな基底クラス

コンパイラ明確を解決できませんでした関数呼び出し、関数が 1 つ以上の基底クラスに存在するためです。

このエラーを解決するには、継承から基底クラスのいずれかを削除するか、関数呼び出しを明示的に修飾します。

次の例では、C2387 が生成されます。

```
// C2387.cpp
namespace N1 {
   struct B {
      virtual void f() {
      }
   };
}

namespace N2 {
   struct B {
      virtual void f() {
      }
   };
}

struct D : N1::B, N2::B {
   virtual void f() {
      B::f();   // C2387
      // try the following line instead
      // N1::B::f();
   }
};

int main() {
   D aD;
   aD.f();
}
```