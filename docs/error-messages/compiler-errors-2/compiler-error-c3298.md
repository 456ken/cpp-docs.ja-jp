---
title: コンパイラ エラー C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: fe6913d402c6ce4df3551c159eb56a12590799cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222532"
---
# <a name="compiler-error-c3298"></a>コンパイラ エラー C3298

'constraint_1': 'constraint_2' を制約として使用できません。'constraint_2' は ref 制約を含んでおり、'constraint_1' は値の制約を含んでいるためです

制約に相互に排他的な特性を指定することはできません。 たとえば、ジェネリック型パラメーターを、値型と参照型の両方に制限することはできません。

詳細については、次を参照してください。[ジェネリック型パラメーターの制約 (C +/cli CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)します。

## <a name="example"></a>例

次の例では C3298 が生成されます。

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```