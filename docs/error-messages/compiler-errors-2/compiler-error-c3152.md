---
title: コンパイラ エラー C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: 270d2fb02365f9c2460257d96bb5f6028707553e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374886"
---
# <a name="compiler-error-c3152"></a>コンパイラ エラー C3152

'construct': 'keyword' はクラス、構造体、または仮想メンバー関数にのみ適用できます

特定のキーワードは、C++ クラスにのみ適用できます。

次の例では C3152 が生成され、その修正方法が示されています。

```
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
