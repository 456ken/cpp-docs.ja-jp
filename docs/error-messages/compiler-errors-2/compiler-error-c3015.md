---
title: コンパイラ エラー C3015
ms.date: 11/04/2016
f1_keywords:
- C3015
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
ms.openlocfilehash: 97ad6b51b9444e03f17511e26be75f5a783a5f07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350271"
---
# <a name="compiler-error-c3015"></a>コンパイラ エラー C3015

OpenMP 'for' ステートメントの初期化には、正しくない形式が含まれています

OpenMP ステートメントの `for` ループを完全かつ明示的に指定する必要があります。

次の例では C3015 が生成されます。

```
// C3015.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (; i < 0; i += j)   // C3015
      // Try the following line instead:
      // for (i = 0; i < 0; i++)
         --j;
   }
}
```