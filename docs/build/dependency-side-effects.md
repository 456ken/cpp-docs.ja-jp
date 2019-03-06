---
title: 依存関係の副作用
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: 1479fac4defa45545ffd06ab30fd53ae0c2506af
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422638"
---
# <a name="dependency-side-effects"></a>依存関係の副作用

ターゲットが、異なる場所に 2 つの依存関係の行では、コロン (:) を指定し、行の 1 つだけの後にコマンドが表示される場合は、隣接する、または、まるで (nmake の) の依存関係は解釈します。 コマンドがありませんが、代わりにで依存関係はブロックの 1 つの説明に属しているし、他の依存関係に指定されたコマンドを実行する依存関係の推論規則は呼び出しません。 たとえば、これは、ルールの設定。

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

この評価されます。

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

2 つのコロンの場合この効果は発生しません (`::`) が使用されます。 たとえば、これは、ルールの設定。

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

この評価されます。

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>関連項目

[ターゲット](../build/targets.md)
