---
title: コンパイラ エラー C3113
ms.date: 11/04/2016
f1_keywords:
- C3113
helpviewer_keywords:
- C3113
ms.assetid: 3afdc668-b29e-474e-9ea3-aa027d42db7c
ms.openlocfilehash: b8edd31db87587887d9e96522802ee9091caab91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404131"
---
# <a name="compiler-error-c3113"></a>コンパイラ エラー C3113

'structure' がテンプレートまたはジェネリックにすることはできません。

ジェネリック インターフェイスまたは列挙型クラス テンプレートまたはクラスを作成しようとしました。

次の例では、C3113 が生成されます。

```
// C3113.cpp
// compile with: /c
template <class T>
enum E {};   // C3113
// try the following line instead
// class MyClass{};
```