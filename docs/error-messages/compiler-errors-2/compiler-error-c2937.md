---
title: コンパイラ エラー C2937
ms.date: 11/04/2016
f1_keywords:
- C2937
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
ms.openlocfilehash: 8ad25dbcec4ee8a8ed49449cf9e64ebae4af1321
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366526"
---
# <a name="compiler-error-c2937"></a>コンパイラ エラー C2937

'class': type-class-id がグローバル typedef として再定義されています

ジェネリック クラスまたはテンプレート クラスをグローバル `typedef`として使用することはできません。

次の例では C2937 が生成されます。

```
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

C2937 は、ジェネリックを使用しているときも発生する場合があります。

```
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```