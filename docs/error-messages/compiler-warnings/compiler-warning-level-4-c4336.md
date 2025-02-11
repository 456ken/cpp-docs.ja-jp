---
title: コンパイラの警告 (レベル 4) C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: 4946b932fa897dab057e430f16c781e2d06bebd0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400852"
---
# <a name="compiler-warning-level-4-c4336"></a>コンパイラの警告 (レベル 4) C4336

クロスレファレンスしたタイプ ライブラリ 'type_lib1' を 'type_lib2' をインポートする前にインポートします。

タイプ ライブラリが参照された、 [#import](../../preprocessor/hash-import-directive-cpp.md)ディレクティブ。 ただし、タイプ ライブラリがで参照されていませんでしたが、別のタイプ ライブラリへの参照に含まれる`#import`します。 この他の .tlb ファイルは、コンパイラによって検出されました。

(Midl.exe でコンパイルされた) 次の 2 つのファイルから作成したディスクの特定の 2 つのタイプ ライブラリ:

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

2 つ目のタイプ ライブラリ:

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

次の例では、C4336 が生成されます。

```
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```