---
title: コンパイラ エラー C2691
ms.date: 11/04/2016
f1_keywords:
- C2691
helpviewer_keywords:
- C2691
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
ms.openlocfilehash: 34287b785532394d33e94e37e7a6a9955d935f14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360197"
---
# <a name="compiler-error-c2691"></a>コンパイラ エラー C2691

'data type': マネージまたは WinRTarray がこの要素の型を含めることはできません

マネージド配列または WinRT 配列の要素の型は、値型または参照型になります。

次の例では C2691 が生成されます。

```
// C2691a.cpp
// compile with: /clr
class A {};

int main() {
   array<A>^ a1 = gcnew array<A>(20);   // C2691
   array<int>^ a2 = gcnew array<int>(20);   // value type OK
}
```
