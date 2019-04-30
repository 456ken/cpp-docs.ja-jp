---
title: コンパイラ エラー C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 1e2f8e8cd38b90a698994743609892896ef0d1a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406900"
---
# <a name="compiler-error-c2825"></a>コンパイラ エラー C2825

var: クラスまたは名前空間続く場合があります ':: '

失敗したときは、修飾名を形成しました。

たとえば、コードに関数名が始まる関数宣言が含まれていないことを確認:: です。

## <a name="example"></a>例

次の例では、C2825 が生成されます。

```
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```