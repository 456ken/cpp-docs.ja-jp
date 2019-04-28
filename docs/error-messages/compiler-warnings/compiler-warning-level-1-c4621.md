---
title: コンパイラの警告 (レベル 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: d35c4143d5b90c7a6a49337931dad4ba73804f20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221366"
---
# <a name="compiler-warning-level-1-c4621"></a>コンパイラの警告 (レベル 1) C4621

'operator--' の型 'type'、前置形式を使用していない後置形式

指定した型の定義後置デクリメント演算子がありませんでした。 コンパイラは、オーバーロードされた前置演算子を使用します。

この警告は、後置 `--` 演算子を定義することで回避できます。 引数が 2 つのバージョンを作成、`--`次に示す演算子。

```
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   --a;
   a--;   // C4621
}
```