---
title: コンパイラ エラー C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: e344d06345c0f3a79b86e9cab4e1c5dacb47e9c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173432"
---
# <a name="compiler-error-c3413"></a>コンパイラ エラー C3413

'name': 明示的インスタンス化が無効です

不正な形式の明示的なインスタンス化が検出されました。

次の例では C3413 が生成されます。

```
// C3413.cpp
template
class MyClass {};   // C3413
```

考えられる解決方法:

```
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```