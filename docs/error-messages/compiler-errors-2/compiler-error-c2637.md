---
title: コンパイラ エラー C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: 4231a811911fdf600b47962e929f6f3cff1f1bca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395457"
---
# <a name="compiler-error-c2637"></a>コンパイラ エラー C2637

'identifier': データ メンバーへのポインターを変更することはできません

データ メンバーへのポインターは、呼び出し規約を持つことはできません。 を解決するには、呼び出し規則を削除するかのメンバー関数へのポインターを宣言します。

次の例では、C2637 が生成されます。

```
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```