---
title: コンパイラ エラー C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: dc976a0c16d19d1fd2340676e43eb71903163aa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222859"
---
# <a name="compiler-error-c2627"></a>コンパイラ エラー C2627

'function': メンバー関数は無名共用体では使用できません

[無名共用体](../../cpp/unions.md#anonymous_unions)メンバー関数を含めることはできません。

次の例では、C2627 が生成されます。

```
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```