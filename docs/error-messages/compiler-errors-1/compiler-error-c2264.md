---
title: コンパイラ エラー C2264
ms.date: 11/04/2016
f1_keywords:
- C2264
helpviewer_keywords:
- C2264
ms.assetid: 158b72cc-cee9-4a08-bd79-b7a5955345a8
ms.openlocfilehash: 65f8dc1f6f1ad8514b2a6bda1bbd9645af5c251a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243942"
---
# <a name="compiler-error-c2264"></a>コンパイラ エラー C2264

'function': 関数の定義または宣言以外のエラー関数が呼び出されません

定義が無効または宣言なのため、関数を呼び出すことはできません。

次の例では、C2264 が生成されます。

```
// C2264.cpp
struct C {
   // Delete the following line to resolve.
   operator int(int = 0){}   // incorrect declaration
};

struct D {
   operator int(){return 0;}   // OK
};

int main() {
   int i;

   C c;
   i = c;   // C2264

   D d;
   i = d;   // OK
}
```