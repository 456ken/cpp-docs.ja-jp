---
title: コンパイラ エラー C3766
ms.date: 11/04/2016
f1_keywords:
- C3766
helpviewer_keywords:
- C3766
ms.assetid: b5af2089-2e1e-4e45-a41d-495b6c55656e
ms.openlocfilehash: 2d871e331987cb2731aad8b4fbc6ec2f094bd218
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400228"
---
# <a name="compiler-error-c3766"></a>コンパイラ エラー C3766

'type' がメソッド 'function' には、インターフェイスの実装の提供する必要があります。

インターフェイスから継承するクラスには、インターフェイス メンバーを実装する必要があります。

## <a name="example"></a>例

次の例では、C3766 が生成されます。

```
// C3766.cpp
// compile with: /clr /c

delegate void MyDel();

interface struct IFace {
   virtual event MyDel ^ E;
};

ref struct Class1 : public IFace {};   // C3766

// OK
ref struct Class2 : public IFace {
   virtual event MyDel ^ E {
      void add(MyDel ^) {}
      void remove(MyDel ^) {}
   }
};
```