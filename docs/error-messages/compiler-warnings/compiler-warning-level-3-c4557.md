---
title: コンパイラの警告 (レベル 3) C4557
ms.date: 11/04/2016
f1_keywords:
- C4557
helpviewer_keywords:
- C4557
ms.assetid: 7d9db716-03b2-4ee5-9b09-ba8aa5aa7e4c
ms.openlocfilehash: 5b236559708759cb30487ef9a8fde92cc42889c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401814"
---
# <a name="compiler-warning-level-3-c4557"></a>コンパイラの警告 (レベル 3) C4557

'__assume' は影響 'effect' を含んでいます。

渡される値、 [_assume](../../intrinsics/assume.md)ステートメント 2 が変更されました。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4557 が生成されます。

```
// C4557.cpp
// compile with: /W3
#pragma warning(default : 4557)
int main()
{
   int i;
   __assume(i++);   // C4557
}
```