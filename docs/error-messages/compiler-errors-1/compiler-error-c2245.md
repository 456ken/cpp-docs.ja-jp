---
title: コンパイラ エラー C2245
ms.date: 11/04/2016
f1_keywords:
- C2245
helpviewer_keywords:
- C2245
ms.assetid: 08aaeadf-10ec-485a-b2a6-6e775289082b
ms.openlocfilehash: 53288d86a59fe2cd31ddac4af7766360544c65c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403042"
---
# <a name="compiler-error-c2245"></a>コンパイラ エラー C2245

friend と指定された存在しないメンバー関数 'function' (メンバー関数署名がオーバーロードと一致しません)

フレンドとして指定された関数がコンパイラによって検出されませんでした。

次の例では C2245 が生成されます。

```
// C2245.cpp
// compile with: /c
class B {
   void f(int i);
};

class A {
   int m_i;
   friend void B::f(char);   // C2245
   // try the following line instead
   // friend void B::f(int);
};

void B::f(int i) {
   A a;
   a.m_i = 0;
}
```