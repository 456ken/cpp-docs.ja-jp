---
title: コンパイラの警告 C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: b5afb829485e0e9533a14e818e6d6785f268a83b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772093"
---
# <a name="compiler-warning-c4485"></a>コンパイラの警告 C4485

'override_function': 基本 ref クラス メソッド 'base_class_function' と一致しますがマークされている 'new' または 'override';'new' (および 'virtual') と見なされます

アクセサーのオーバーライドの有無、`virtual`キーワードを基底クラスのアクセサー関数が、`override`または`new`指定子は、オーバーライドする関数のシグネチャの一部であったされません。 追加、`new`または`override`この警告を解決するのには指定子。

参照してください[オーバーライド](../../extensions/override-cpp-component-extensions.md)と[new (新規のスロット vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)詳細についてはします。

C4485 は常に、エラーとして発行されます。 使用して、[警告](../../preprocessor/warning.md)C4485 を抑制するプラグマ。

## <a name="example"></a>例

次のサンプルの生成 C4485

```
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```