---
title: コンパイラの警告 (レベル 2) C4308
ms.date: 11/04/2016
f1_keywords:
- C4308
helpviewer_keywords:
- C4308
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
ms.openlocfilehash: f97d66f9e3445d022adc3362532774b15ea09961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402490"
---
# <a name="compiler-warning-level-2-c4308"></a>コンパイラの警告 (レベル 2) C4308

負の整数定数が符号なしの型に変換

式では、負の整数定数を符号なしの型に変換します。 式の結果は無意味な可能性があります。

## <a name="example"></a>例

```
// C4308.cpp
// compile with: /W2
unsigned int u = (-5 + 3U);   // C4308

int main()
{
}
```