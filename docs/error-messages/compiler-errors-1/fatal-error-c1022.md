---
title: 致命的なエラー C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: 044ebbbe895677acf74977e56879c292486e18cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383140"
---
# <a name="fatal-error-c1022"></a>致命的なエラー C1022

#endif が必要です。

`#if`、 `#ifdef`、 `#ifndef` の各ディレクティブに対応する `#endif` ディレクティブがありません。 各 `#if`、 `#ifdef`、 `#ifndef` に対応する `#endif`を指定してください。

次の例では C1022 が生成されます。

```
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

考えられる解決方法:

```
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```