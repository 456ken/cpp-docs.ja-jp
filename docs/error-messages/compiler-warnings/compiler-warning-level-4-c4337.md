---
title: コンパイラの警告 (レベル 4) C4337
ms.date: 11/04/2016
f1_keywords:
- C4337
helpviewer_keywords:
- C4337
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
ms.openlocfilehash: 2bfa5f9b30fa0325df1c3655ded53ab0525449c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400839"
---
# <a name="compiler-warning-level-4-c4337"></a>コンパイラの警告 (レベル 4) C4337

クロスレファレンスしたタイプ ライブラリ 'typelib1' で 'typelib2' が自動的にインポートされています。

Auto_search 属性[#import ディレクティブ](../../preprocessor/hash-import-directive-cpp.md)暗黙的にインポートするタイプ ライブラリの原因となった。

(Midl.exe でコンパイルされた) 次の 2 つのファイルから作成したディスクの特定の 2 つのタイプ ライブラリ:

```
// C4337a.idl
[
  uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12B)
]
library C4337aLib
{
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12C)]
   enum E_C4337a
   {
      one = 0,
      two = 1,
      three = 2
    };
};
```

2 つ目 .idl ファイル

```
// C4337b.idl
[
   uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12D)
]

library C4337bLib
{
   importlib("c4337a.tlb");

   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12E)]
   struct S_C4337b
   {
      enum E_C4337a e;
   };
};
```

次の例では、C4337 が生成されます。

```
// C4337.cpp
// compile with: /W4 /LD
#import "c4337b.tlb" auto_search   // C4337
// explicitly #import all type libraries to resolve
// #import "C4337a.tlb"
// #import "C4337b.tlb"
```