---
title: コンパイラの警告 (レベル 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 24872bb0b42de77dde358dc29f99826b41638628
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401346"
---
# <a name="compiler-warning-level-4-c4131"></a>コンパイラの警告 (レベル 4) C4131

'function': 旧スタイルの宣言が使われています

指定された関数の宣言は、プロトタイプ形式ではありません。

旧スタイルの関数の宣言をプロトタイプ形式に変換する必要があります。

旧スタイルの関数の宣言の例を次に示します。

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

プロトタイプ形式の例を次に示します。

```
void addrec( char *name, int id )
{ }
```