---
title: コンパイラ エラー C2181
ms.date: 11/04/2016
f1_keywords:
- C2181
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
ms.openlocfilehash: a676794b5dedd17cfb973de36d3771ef1130a786
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386097"
---
# <a name="compiler-error-c2181"></a>コンパイラ エラー C2181

else 文が if と一致しません。

各 `else` には一致する `if`が必要です。

次の例では C2181 が生成されます。

```
// C2181.cpp
int main() {
   int i = 0;
   else   // C2181
      i = 1;
}
```

考えられる解決方法:

```
// C2181b.cpp
int main() {
   int i = 0;
   if(i)
      i = 0;
   else
      i = 1;
}
```