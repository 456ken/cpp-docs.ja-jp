---
title: コンパイラの警告 (レベル 4) C4263
ms.date: 11/04/2016
f1_keywords:
- C4263
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
ms.openlocfilehash: a035646aab2589523adb9eb0b201e2d4d781632c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400930"
---
# <a name="compiler-warning-level-4-c4263"></a>コンパイラの警告 (レベル 4) C4263

'function': メンバー関数はどの基底クラス仮想メンバー関数をオーバーライドしません

クラスの関数定義では、同じ数または引数の型ではありませんが、基底クラスの仮想関数と同じ名前が。 実質的に、基底クラスで仮想関数は隠されます。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4263 が生成されます。

```
// C4263.cpp
// compile with: /W4
#pragma warning(default:4263)
#pragma warning(default:4264)
class B {
public:
   virtual void func();
};

class D : public B {
   void func(int);   // C4263
};

int main() {
}
```