---
title: コンパイラ エラー C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376251"
---
# <a name="compiler-error-c3136"></a>コンパイラ エラー C3136

'interface': COM インターフェイスは、別の COM インターフェイスからのみ継承できます、'interface' は COM インターフェイスはありません。

適用されているインターフェイス、[インターフェイス属性](../../windows/attributes/interface-attributes.md)COM インターフェイスではないインターフェイスから継承します。 COM インターフェイスが最終的に継承`IUnknown`します。 インターフェイス属性に続く任意のインターフェイスは、COM インターフェイスです。

次の例では、C3136 が生成されます。

```
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```