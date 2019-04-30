---
title: コンパイラ エラー C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 503f295d62c598e3138b1a001d6b350c0d90ea84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385447"
---
# <a name="compiler-error-c3898"></a>コンパイラ エラー C3898

'var': 型のデータ メンバーのマネージ型のメンバーであることができますのみ

[Initonly](../../dotnet/initonly-cpp-cli.md)データ メンバーは、ネイティブ クラスで宣言されました。  `initonly`データ メンバーは、CLR クラスでのみ宣言できます。

次の例では、C3898 が生成されます。

```
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

考えられる解決方法:

```
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```