---
title: コンパイラの警告 (レベル 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: c8f0bb514a3da932500f986e50a20af0947827c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403988"
---
# <a name="compiler-warning-level-4-c4343"></a>コンパイラの警告 (レベル 4) C4343

\#プラグマ optimize("g",off)/Og オプションをオーバーライドします。

この警告 (Itanium プロセッサ ファミリ (IPF) コンパイラでのみ有効) は、pragma [optimize](../../preprocessor/optimize.md) が [/Og](../../build/reference/og-global-optimizations.md) コンパイラ オプションをオーバーライドしたことを報告します。

次の例では C4343 が生成されます。

```
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```