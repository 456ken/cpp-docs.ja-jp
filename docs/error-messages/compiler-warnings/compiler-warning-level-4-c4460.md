---
title: コンパイラの警告 (レベル 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: a42562a2c35bb56de4ce7147e199f4db2dddb684
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400813"
---
# <a name="compiler-warning-level-4-c4460"></a>コンパイラの警告 (レベル 4) C4460

WinRT 演算子または CLR 演算子 'operator' は参照によって渡されたパラメーターを含んでいます。 WinRT 演算子または CLR 演算子 'operator' は C++ 演算子 'operator' とは異なる意味を示します。値によって渡すことを意図しましたか?

ユーザー定義の Windows ランタイム演算子または CLR 演算子に参照で値を渡しました。 値が関数内で変更された場合、関数の呼び出し後の戻り値が関数の戻り値に割り当てられることに注意してください。 標準 C++ では、関数の呼び出し後、変更された値が反映されます。

## <a name="example"></a>例

次の例では C4460 を生成し、その修正方法を示しています。

```
// C4460.cpp
// compile with: /W4 /clr
#include <stdio.h>

public value struct V {
   static V operator ++(V& me) {   // C4460
   // try the following line instead
   // static V operator ++(V me) {

      printf_s(__FUNCSIG__ " called\n");
      V tmp = me;
      me.m_i++;
      return tmp;
   }
   int m_i;
};

int main() {
   V v;
   v.m_i = 0;

   printf_s("%d\n", v.m_i);   // Should print 0
   v++;   // Translates to "v = V::operator ++(v)"
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning
}
```