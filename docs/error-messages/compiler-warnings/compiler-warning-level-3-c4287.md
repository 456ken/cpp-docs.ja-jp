---
title: コンパイラの警告 (レベル 3) C4287
ms.date: 11/04/2016
f1_keywords:
- C4287
helpviewer_keywords:
- C4287
ms.assetid: 1bf3bff8-6402-4d06-95ba-431678a790a7
ms.openlocfilehash: da051bb27ec877fd6347469c9f06b09bd4e0db32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402100"
---
# <a name="compiler-warning-level-3-c4287"></a>コンパイラの警告 (レベル 3) C4287

'operator': 符号なし/負の定数が一致しません

符号なしの変数は、負の値を使用して、操作で使用されました。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

## <a name="example"></a>例

次の例では、C4287 が生成されます。

```
// C4287.cpp
// compile with: /W3
#pragma warning(default : 4287)
#include <stdio.h>

int main()
{
    unsigned int u = 1;
    if (u < -1)   // C4287
        printf_s("u LT -1");
    else
        printf_s("u !LT -1");
    return 0;
}
```