---
title: コンパイラの警告 (レベル 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 762f52c9f051a660cce68d424e02fc45422376e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302281"
---
# <a name="compiler-warning-level-1-c4142"></a>コンパイラの警告 (レベル 1) C4142

問題のない型の再定義しています

型は、生成されたコードに影響が方法で再定義しません。

次のような原因をチェックして問題を解決するには:

- 派生クラスのメンバー関数は、基底クラスのメンバー関数は、対応するからさまざまな戻り値の型。

- 定義されている型、`typedef`別の構文を使用して、コマンドが再定義します。

次の例では、C4142 が生成されます。

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```