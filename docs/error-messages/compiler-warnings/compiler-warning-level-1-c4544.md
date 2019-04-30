---
title: コンパイラの警告 (レベル 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: f2a3f2e64a6a859add8182de4fc883c735563e92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352924"
---
# <a name="compiler-warning-level-1-c4544"></a>コンパイラの警告 (レベル 1) C4544

' declaration':既定のテンプレート引数がこのテンプレート宣言では無視されます。

既定のテンプレート引数は誤った場所で指定されたため、無視されました。 クラス テンプレートの既定のテンプレート引数を指定できるのは、クラス テンプレートのメンバーではなく、クラス テンプレートの宣言または定義でのみです。

次の例では、C4545 を生成し、その修正方法を示しています。

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

次の例では、既定のパラメーターがクラス テンプレート `S` に適用されます。

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```