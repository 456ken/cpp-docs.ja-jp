---
title: コンパイラ エラー C2998
ms.date: 11/04/2016
f1_keywords:
- C2998
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
ms.openlocfilehash: 16a3319e71d465082120cbc58e3c7c6b916be80f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393611"
---
# <a name="compiler-error-c2998"></a>コンパイラ エラー C2998

'identifier': テンプレート定義ではありません

コンパイラはテンプレート定義で使用されている構文を処理できませんでした。

次の例では C2998 が生成されます。

```
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```