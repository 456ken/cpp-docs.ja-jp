---
title: コンパイラ エラー C2908
ms.date: 11/04/2016
f1_keywords:
- C2908
helpviewer_keywords:
- C2908
ms.assetid: 49cd2a21-cad8-4ba0-9a0b-3a0190d9344c
ms.openlocfilehash: f798be5ef93eb3f072036888b800fa4008fa2de9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408564"
---
# <a name="compiler-error-c2908"></a>コンパイラ エラー C2908

明示的な特殊化です。'template' は既にインスタンス化されています

プライマリ テンプレートの特殊化は、明示的な特殊化する前に発生します。

次の例では、C2908 が生成されます。

```
// C2908.cpp
// compile with: /c
template<class T> class X {};

void f() {
X<int> x;   //specialization and instantiation
            //of X<int>
}

template<> class X<int> {}  // C2908, explicit specialization
```