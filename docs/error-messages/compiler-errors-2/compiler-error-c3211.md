---
title: コンパイラ エラー C3211
ms.date: 11/04/2016
f1_keywords:
- C3211
helpviewer_keywords:
- C3211
ms.assetid: 85e33fed-3b59-4315-97e6-20d31c6a985a
ms.openlocfilehash: 6de2129a1cdd6391245148816b29faa65d7e8721
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311762"
---
# <a name="compiler-error-c3211"></a>コンパイラ エラー C3211

'explicit specialization': 明示的特殊化は、部分的特殊化の構文を使用しています。代わりに、テンプレート <> を使用してください

明示的特殊化の形式が正しくありません。

次の例では C3211 が生成されます。

```
// C3211.cpp
// compile with: /LD
template<class T>
struct s;

template<class T>
// use the following line instead
// template<>
struct s<int>{};   // C3211
```