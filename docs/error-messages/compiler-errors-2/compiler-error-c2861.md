---
title: コンパイラ エラー C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: bb61272b5a8d94a26096bd05260de331e853bf0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329077"
---
# <a name="compiler-error-c2861"></a>コンパイラ エラー C2861

'関数の name': インターフェイスのメンバー関数を定義することはできません

メンバーを検出し、コンパイラは、interface キーワードが発生しましたか、インターフェイスとして構造体を推測が関数の定義。  インターフェイスは、メンバー関数の定義を含めることはできません。

## <a name="example"></a>例

次の例では、C2861 が生成されます。

```
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861
```