---
title: コンパイラ エラー C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: f35e384a5b242eb28427e1ff62ac55a3e9b206c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388867"
---
# <a name="compiler-error-c2279"></a>コンパイラ エラー C2279

例外の指定は、typedef 宣言に記述できません。

**/Za**、[例外仕様](../../cpp/exception-specifications-throw-cpp.md)typedef 宣言では許可されません。

次の例では、C2279 が生成されます。

```
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```