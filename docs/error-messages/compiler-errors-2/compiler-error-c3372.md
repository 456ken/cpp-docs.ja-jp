---
title: コンパイラ エラー C3372
ms.date: 11/04/2016
f1_keywords:
- C3372
helpviewer_keywords:
- C3372
ms.assetid: 38ee39ed-03ff-4e6d-9104-f1977b96645d
ms.openlocfilehash: f410e18621c6784de011d12b45d07c163afdb1c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400345"
---
# <a name="compiler-error-c3372"></a>コンパイラ エラー C3372

最低 1 つのインターフェイスをコクラスの属性 'source' に指定しなければなりません

特定の属性では、パラメーターとしてインターフェイス名を渡す必要があります。

次の例では C3372 が生成されます。

```
// C3372.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface {
   HRESULT f1();
};
// to resolve, pass an interface name to the source attribute
// for example, source(IMyIface)
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), source,
  default(IMyIface) ] // C3372
class CMyClass {
};

int main() {
}
```