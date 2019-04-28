---
title: コンパイラ エラー C2160
ms.date: 11/04/2016
f1_keywords:
- C2160
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
ms.openlocfilehash: bd0c49f44bce09958541a47db0c66bc22d7f2b76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174836"
---
# <a name="compiler-error-c2160"></a>コンパイラ エラー C2160

マクロ定義がトークン連結演算子 (##) で始まっています。

マクロ定義がトークン連結演算子 (##) で始まっています。

次の例では C2160 が生成されます。

```
// C2160.cpp
// compile with: /c
#define mac(a,b) #a   // OK
#define mac(a,b) ##a   // C2160
```