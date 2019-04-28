---
title: コンパイラ エラー C3236
ms.date: 11/04/2016
f1_keywords:
- C3236
helpviewer_keywords:
- C3236
ms.assetid: 4ef1871f-a348-44ae-922b-1e2081de20d0
ms.openlocfilehash: 2bcc9aa2c1b179caf6c7fc51ba86cdc4e56b0a5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175512"
---
# <a name="compiler-error-c3236"></a>コンパイラ エラー C3236

generic の明示的なインスタンス生成は使用できません

コンパイラでは、ジェネリック クラスを明示的にインスタンス化できません。

次の例では C3236 が生成されます。

```
// C3236.cpp
// compile with: /clr
generic<class T>
public ref class X {};

generic ref class X<int>;   // C3236
```

次の例では、考えられる解決策を示しています。

```
// C3236b.cpp
// compile with: /clr /c
generic<class T>
public ref class X {};
```