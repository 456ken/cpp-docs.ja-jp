---
title: コンパイラの警告 (レベル 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 96e1077ce3c9e60823a11aa41719738265ee703b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345384"
---
# <a name="compiler-warning-level-2-c4285"></a>コンパイラの警告 (レベル 2) C4285

戻り値の型の 'identifier::operator ->' は再帰挿入辞表記を使用して適用されている場合

指定した**演算子**関数の型を返すことは定義されているかが定義されている型への参照。

次の例では、C4285 が生成されます。

```
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```