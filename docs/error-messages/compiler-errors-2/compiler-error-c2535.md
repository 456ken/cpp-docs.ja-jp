---
title: コンパイラ エラー C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: b2b5452cfe59284d56b019674ffbabbda0dc62d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574024"
---
# <a name="compiler-error-c2535"></a>コンパイラ エラー C2535

'identifier' : メンバー関数は、既に定義または宣言されています。

このエラーは、オーバーロードされた関数の定義または宣言で、同じ仮パラメーター リストを繰り返し使用した場合に発生します。

Dispose 関数が原因で C2535 が発生した場合は、[デストラクターおよびファイナライザー](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)詳細についてはを参照してください。

次の例では、C2535 が生成されます。

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```