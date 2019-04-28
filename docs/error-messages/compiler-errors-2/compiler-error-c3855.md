---
title: コンパイラ エラー C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: 12ee1c6aa5f414a9cf3084831c956514593102c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265465"
---
# <a name="compiler-error-c3855"></a>コンパイラ エラー C3855

'class': 型パラメーター 'param' には、宣言と互換性がありません

非型テンプレート、または異なる名前を持つジェネリック パラメーターが見つかりました。 これは、テンプレートの特殊化の定義で指定したテンプレート パラメーターは、その宣言と互換性がないときに発生します。

次の例では、C3855 が生成されます。

```
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

考えられる解決方法:

```
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

C3855 は、ジェネリックを使用しているときにも発生します。

```
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

考えられる解決方法:

```
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```