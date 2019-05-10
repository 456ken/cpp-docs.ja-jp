---
title: コンパイラの警告 C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: fe765fa49b9aa11667e1eac4a9cfed54bb84fd8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447865"
---
# <a name="compiler-warning-c4430"></a>コンパイラの警告 C4430

型指定子がありません - int と仮定しました。 メモ:C++ は int を既定値をサポートしていません

このエラーは、Visual Studio 2005 で行ったコンパイラ準拠作業の結果として生成されることができますすべての宣言は、型を明示的に指定する必要があります。int が想定されなくなります。

C4430 がエラーとして常に発行されます。  この警告をオフにすることができます、`#pragma warning`または **/wd**; を参照してください[警告](../../preprocessor/warning.md)または[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、//we、/wo、/Wv、/WX (警告レベル)](../../build/reference/compiler-option-warning-level.md)詳細についてはします。

## <a name="example"></a>例

次の例では、C4430 が生成されます。

```
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```