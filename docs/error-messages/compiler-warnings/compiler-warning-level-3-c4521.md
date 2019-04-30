---
title: コンパイラの警告 (レベル 3) C4521
ms.date: 11/04/2016
f1_keywords:
- C4521
helpviewer_keywords:
- C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
ms.openlocfilehash: 887526810f7e65280adcde422ef871a67ccdde1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401918"
---
# <a name="compiler-warning-level-3-c4521"></a>コンパイラの警告 (レベル 3) C4521

'class': 指定された複数のコピー コンス トラクター

クラスには、1 つの型の複数のコピー コンス トラクターがあります。 この警告は参照用です。コンス トラクターは、プログラムで呼び出し可能です。

使用して、[警告](../../preprocessor/warning.md)この警告を抑制するプラグマ。

## <a name="example"></a>例

次の例では、C4521 が生成されます。

```
// C4521.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A() { cout << "A's default constructor" << endl; }
   A( A &o ) { cout << "A&" << endl; }
   A( const A &co ) { cout << "const A&" << endl; }   // C4521
};

int main() {
   A o1;         // Calls default constructor.
   A o2( o1 );   // Calls A( A& ).
   const A o3;   // Calls default constructor.
   A o4( o3 );   // Calls A( const A& ).
}
```