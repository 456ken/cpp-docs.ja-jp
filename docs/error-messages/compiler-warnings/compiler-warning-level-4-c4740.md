---
title: コンパイラの警告 (レベル 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 936dfb5464eabe7b1ac44df24445224fb9e204a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187031"
---
# <a name="compiler-warning-level-4-c4740"></a>コンパイラの警告 (レベル 4) C4740

インライン asm コードの内外でのフローは、グローバルな最適化を抑制します。

またはのにジャンプ先がある場合に、`asm`ブロック、その関数のグローバルの最適化を無効にします。

次の例では、C4740 が生成されます。

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```