---
title: コンパイラの警告 (レベル 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 98ea72bef0cb95163604144c1069a13c3b27d81c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324533"
---
# <a name="compiler-warning-level-1-c4630"></a>コンパイラの警告 (レベル 1) C4630

'symbol': 'extern' ストレージ クラス指定子のメンバーの定義が無効です

データ メンバーまたはメンバー関数とは見なさ`extern`します。 メンバーは、オブジェクト全体のことができますが、外部、することはできません。 コンパイラは無視、`extern`キーワード。 次の例では、C4630 が生成されます。

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```