---
title: コンパイラ エラー C3655
ms.date: 11/04/2016
f1_keywords:
- C3655
helpviewer_keywords:
- C3655
ms.assetid: 724919ab-2915-4b61-8794-44648e162d62
ms.openlocfilehash: 7a13d4d7c08f6510e5ab71c07c31baa9359b47b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227123"
---
# <a name="compiler-error-c3655"></a>コンパイラ エラー C3655

'function': 関数は明示的にオーバーライドされて既に

関数のみに明示的にオーバーライドできます 1 回です。 詳細については、次を参照してください。[明示的なオーバーライド](../../extensions/explicit-overrides-cpp-component-extensions.md)します。

次の例では、C3655 が生成されます。

```
// C3655.cpp
// compile with: /clr /c
public ref struct B {
   virtual void f();
   virtual void g();
};

public ref struct D : B {
   virtual void f() new sealed = B::f;
   virtual void g() new sealed = B::f;   // C3655
   // try the following line instead
   // virtual void g() new sealed = B::g;
};
```