---
title: コンパイラ エラー C2766
ms.date: 11/04/2016
f1_keywords:
- C2766
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
ms.openlocfilehash: 87ea9f693265080d744746c6a8014b2b8b6db13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257557"
---
# <a name="compiler-error-c2766"></a>コンパイラ エラー C2766

明示的な特殊化です。'specialization' は既に定義されています

重複する明示的な特殊化は許可されません。 詳細については、次を参照してください。[関数テンプレートの明示的な特殊化](../../cpp/explicit-specialization-of-function-templates.md)します。

次の例では、C2766 が生成されます。

```
// C2766.cpp
// compile with: /c
template<class T>
struct A {};

template<>
struct A<int> {};

template<>
struct A<int> {};   // C2766
// try the following line instead
// struct A<char> {};
```