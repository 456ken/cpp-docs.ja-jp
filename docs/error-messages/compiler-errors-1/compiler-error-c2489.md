---
title: コンパイラ エラー C2489
ms.date: 11/04/2016
f1_keywords:
- C2489
helpviewer_keywords:
- C2489
ms.assetid: 67d8cd98-db7e-4f7f-86b4-4af7bc89ec8b
ms.openlocfilehash: e4024455e17956fc67917e92a3ca531eca5c5e04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361036"
---
# <a name="compiler-error-c2489"></a>コンパイラ エラー C2489

'identifier': 'naked' 関数では関数スコープで許可されません auto またはレジスタ変数の初期化

詳細については、次を参照してください。 [naked](../../cpp/naked-cpp.md)します。

次の例では、C2489 が生成されます。

```
// C2489.cpp
// processor: x86
__declspec( naked ) int func() {
   int i = 1;   // C2489
   register int j = 1;   // C2489
}
```