---
title: コンパイラ エラー C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 9fe9b765af72a8864e3e899cafcf648a9facb67e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182796"
---
# <a name="compiler-error-c2289"></a>コンパイラ エラー C2289

同じ型の修飾子が 2 度以上使われています。

型の宣言または定義で、型修飾子 (`const`、 `volatile`、 `signed`、または `unsigned`) が 2 回以上使用されています。ANSI 互換のオプション (**/Za**) を指定している場合はエラーになります。

次の例では C2286 が生成されます。

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```