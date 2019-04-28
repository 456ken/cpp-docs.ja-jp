---
title: コンパイラ エラー C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2b3288d02c611bf6785ca1ea7757e2283d889050
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328636"
---
# <a name="compiler-error-c3453"></a>コンパイラ エラー C3453

'attribute': 修飾子 'assembly' が一致しなかったため、属性は適用されませんでした

アセンブリ レベルまたはモジュール レベルの属性は、スタンドアロンの命令としてのみ指定できます。

## <a name="example"></a>例

次の例では C3453 が生成されます。

```
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```