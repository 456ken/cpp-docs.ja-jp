---
title: コンパイラの警告 (レベル 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221034"
---
# <a name="compiler-warning-level-4-c4516"></a>コンパイラの警告 (レベル 4) C4516

'class::symbol' : access-declarations are deprecated; member using-declarations provide a better alternative

ANSI C++ 委員会には、アクセスの宣言が宣言されている (せずに、派生クラスのメンバーのアクセスを変更して、[を使用して](../../cpp/using-declaration.md)キーワード) に期限切れであります。 Access 宣言は、C++ の将来のバージョンでサポートされていません可能性があります。

次の例では、C4516 が生成されます。

```
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```