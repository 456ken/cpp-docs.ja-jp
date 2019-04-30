---
title: コンパイラ エラー C3183
ms.date: 11/04/2016
f1_keywords:
- C3183
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
ms.openlocfilehash: 232e9999bc31ac3e01833e7982acfb03e9d0afaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382373"
---
# <a name="compiler-error-c3183"></a>コンパイラ エラー C3183

マネージド型または WinRT 型 'type' の中で名前のないクラス、構造体またはユニオンを定義することはできません。

マネージド型または WinRT 型に埋め込まれる型の名前を指定する必要があります。

次の例では C3183 エラーが生成されます。

```
// C3183a.cpp
// compile with: /clr /c
ref class Test
{
   ref class
   {  // C3183, delete class or name it
      int a;
      int b;
   };
};
```
