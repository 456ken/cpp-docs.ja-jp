---
title: コンパイラ エラー C3131
ms.date: 11/04/2016
f1_keywords:
- C3131
helpviewer_keywords:
- C3131
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
ms.openlocfilehash: 082839c01a2da4b0d149962367b9719932d2b272
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349933"
---
# <a name="compiler-error-c3131"></a>コンパイラ エラー C3131

プロジェクトが、'module' 属性 'name' プロパティがあります。

[モジュール](../../windows/module-cpp.md)属性には、名前のパラメーターが必要です。

次の例では、C3131 が生成されます。

```
// C3131.cpp
[emitidl];
[module];   // C3131
// try the following line instead
// [module (name="MyLib")];

[public]
typedef long int LongInt;
```