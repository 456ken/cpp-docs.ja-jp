---
title: コンパイラ エラー C2195
ms.date: 11/04/2016
f1_keywords:
- C2195
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
ms.openlocfilehash: 9d0fdb3623a86adb07e910b186305f3e468d24b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174537"
---
# <a name="compiler-error-c2195"></a>コンパイラ エラー C2195

'identifier': データ セグメントです

`code_seg`プラグマで使用されるセグメント名を使用して、`data_seg`プラグマ。

次の例では、C2195 が生成されます。

```
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```