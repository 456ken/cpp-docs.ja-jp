---
title: コンパイラ エラー C3192
ms.date: 11/04/2016
f1_keywords:
- C3192
helpviewer_keywords:
- C3192
ms.assetid: 8b0083d4-706f-46f6-858a-e1d9af464cf8
ms.openlocfilehash: 685657857b2ed41c29c704633b07dc677fc32fc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382308"
---
# <a name="compiler-error-c3192"></a>コンパイラ エラー C3192

構文エラー: '^' プレフィックス演算子ではありません (候補' *' ですか?)

ハンドルは、逆参照演算子として使用できません。

次の例では、C3192 が生成されます。

```
// C3192.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   MyClass () {}
   MyClass(MyClass%) {}
};

int main() {
   MyClass ^ s = gcnew MyClass;
   MyClass b = ^s;   // C3192

   // OK
   MyClass b2 = *s;
}
```