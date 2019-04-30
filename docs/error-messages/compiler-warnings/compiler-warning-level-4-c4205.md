---
title: コンパイラの警告 (レベル 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 1b165d2bdb2fb50df89fdd77c734c054a40b6e95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401229"
---
# <a name="compiler-warning-level-4-c4205"></a>コンパイラの警告 (レベル 4) C4205

標準の拡張機能を使用: 関数のスコープ内で静的関数の宣言

Microsoft 拡張機能 (/Ze) で**静的**関数は、別の関数内で宣言することができます。 関数には、グローバル スコープが与えられます。

## <a name="example"></a>例

```
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

このような初期化が有効で ANSI 互換でない ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。