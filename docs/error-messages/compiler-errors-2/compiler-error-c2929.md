---
title: コンパイラ エラー C2929
ms.date: 11/04/2016
f1_keywords:
- C2929
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
ms.openlocfilehash: fe2a56f7722c70c11e980fb6ee59230ffd056c5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385720"
---
# <a name="compiler-error-c2929"></a>コンパイラ エラー C2929

'identifier': 明示的なインスタンス生成。明示的にテンプレート クラス メンバーのインスタンス生成を行ったり抑制したりできません

識別子がインスタンス化できないようになっている間は、識別子を明示的にインスタンス化することはできません。

次の例では C2929 が生成されます。

```
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```