---
title: コンパイラ エラー C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: 2df788efd93fb531822d858ea5aee1722487db81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387043"
---
# <a name="compiler-error-c2261"></a>コンパイラ エラー C2261

'string': アセンブリ参照が有効でないし、解決することはできません

値が無効です。

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> フレンド アセンブリの指定に使用されます。 たとえば、a.dll b.dll をフレンド アセンブリとして指定する場合は、(a.dll) の指定は。InternalsVisibleTo("b") します。 ランタイムには、b.dll a.dll (プライベート型) を除くのすべてのアクセスが許可されます。

フレンド アセンブリを指定するときに、正しい構文の詳細は、次を参照してください。[フレンド アセンブリ (C++)](../../dotnet/friend-assemblies-cpp.md)します。

## <a name="example"></a>例

次の例では、C2261 が生成されます。

```
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```