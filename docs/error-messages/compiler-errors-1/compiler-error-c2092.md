---
title: コンパイラ エラー C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: d3d0b0e62fbc5f8ad90b3fee5fe39c6bdaba7c2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376010"
---
# <a name="compiler-error-c2092"></a>コンパイラ エラー C2092

'名をアレイ' 配列要素の型が関数にすることはできません。

関数の配列を指定することはできません。 関数へのポインターの配列を使用します。

## <a name="example"></a>例

次の例では、C2092 が生成されます。

```
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

## <a name="example"></a>例

考えられる解決方法:

```
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```