---
title: コンパイラの警告 (レベル 1) C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 1032261c39e0a285ac686e09573161de3b46e0e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324546"
---
# <a name="compiler-warning-level-1-c4615"></a>コンパイラの警告 (レベル 1) C4615

\#pragma 警告: 不明な警告型

無効な警告指定子が使用されていた**プラグマ**[警告](../../preprocessor/warning.md)します。 エラーを解決するには、有効な警告指定子を使用します。

次の例では、C4615 が生成されます。

```
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```