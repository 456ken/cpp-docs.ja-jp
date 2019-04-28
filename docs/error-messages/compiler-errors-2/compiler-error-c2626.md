---
title: コンパイラ エラー C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 434858991c23345e2a6c174c8f323000d42b9b6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222885"
---
# <a name="compiler-error-c2626"></a>コンパイラ エラー C2626

'identifier': プライベートまたはプロテクト データ メンバーは、匿名構造体または共用体では許可されていません

匿名構造体または共用体のメンバーは、パブリック アクセスを持つ必要があります。

次の例では C2626 が生成されます。

```
// C2626.cpp
int main() {
   union {
   protected:
      int j;     // C2626, j is protected
   private:
      int k;     // C2626, k is private
   };
}
```

この問題を解決するには、プライベートまたはプロテクト タグを削除します。

```
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```