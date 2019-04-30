---
title: コンパイラ エラー C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: 66a111ea6fe2ca5acfbc473d19da62d9de67372a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360165"
---
# <a name="compiler-error-c2791"></a>コンパイラ エラー C2791

'super' の不正な使用: 'class' には、すべての基底クラスはありません。

キーワード[super](../../cpp/super.md)すべての基底クラスがないクラスのメンバー関数のコンテキスト内で使用されました。

次の例では、C2791 が生成されます。

```
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```