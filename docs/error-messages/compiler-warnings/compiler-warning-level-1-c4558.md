---
title: コンパイラの警告 (レベル 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: ae4dd6ebfb00441591a4aa1cdd2ecdfbf37f74d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397303"
---
# <a name="compiler-warning-level-1-c4558"></a>コンパイラの警告 (レベル 1) C4558

'value' のオペランドの値が 'lowerbound - upperbound' の範囲外です。

アセンブリ言語命令に渡された値がパラメーターに指定された範囲外です。 値は切り捨てられます。

次の例では、C4558 が生成されます。

```
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```