---
title: コンパイラ エラー C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 872471158d3f8c301a271dd68b2ef36839e2b9c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161168"
---
# <a name="compiler-error-c2705"></a>コンパイラ エラー C2705

'label' : illegal jump into 'exception handler block' scope

実行が内のラベルにジャンプ、 `try` / `catch`、 `__try` / `__except`、 `__try` / `__finally`ブロックします。 詳細については、「[例外処理](../../cpp/exception-handling-in-visual-cpp.md)」を参照してください。

次の例では、C2705 が生成されます。

```
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```