---
title: コンパイラの警告 (レベル 1) C4662
ms.date: 11/04/2016
f1_keywords:
- C4662
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
ms.openlocfilehash: ecd8e757e1724fcd4c08540559eab75f1e4bed46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374613"
---
# <a name="compiler-warning-level-1-c4662"></a>コンパイラの警告 (レベル 1) C4662

明示的なインスタンス化。テンプレート クラス 'identifier1' に 'identifier2' を特定する定義がありません

指定したテンプレート クラスを宣言しましたが、定義していません。

## <a name="example"></a>例

```
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```