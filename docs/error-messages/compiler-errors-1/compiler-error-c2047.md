---
title: コンパイラ エラー C2047
ms.date: 11/04/2016
f1_keywords:
- C2047
helpviewer_keywords:
- C2047
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
ms.openlocfilehash: 50a8ce4ab9d88312b7f91ebb9df068a07fa21aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408876"
---
# <a name="compiler-error-c2047"></a>コンパイラ エラー C2047

'default' が正しくありません。

キーワード `default` は `switch` ステートメントでのみ使用できます。

次の例では C2047 が生成されます。

```
// C2047.cpp
int main() {
   int i = 0;
   default:   // C2047
   switch(i) {
      case 0:
      break;
   }
}
```

考えられる解決方法:

```
// C2047b.cpp
int main() {
   int i = 0;
   switch(i) {
      case 0:
      break;
      default:
      break;
   }
}
```