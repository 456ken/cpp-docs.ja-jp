---
title: コンパイラ エラー C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 7c9c078e72babc85dc7092b8d6414625e9c0db7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410474"
---
# <a name="compiler-error-c3753"></a>コンパイラ エラー C3753

汎用プロパティは許可されていません

ジェネリック パラメーター リストは、マネージ クラス、構造体、または関数でのみ表示できます。

詳細については、次を参照してください。[ジェネリック](../../extensions/generics-cpp-component-extensions.md)と[プロパティ](../../extensions/property-cpp-component-extensions.md)します。

## <a name="example"></a>例

次の例では、C3753 が生成されます。

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```