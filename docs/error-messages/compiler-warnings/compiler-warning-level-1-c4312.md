---
title: コンパイラの警告 (レベル 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 1983d7b89688568b8152372328216c2a814f7bc0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510087"
---
# <a name="compiler-warning-level-1-c4312"></a>コンパイラの警告 (レベル 1) C4312

'操作' :  'type1' からより大きいサイズの 'type2' へ変換します。

この警告は、32 ビット値を 64 ビット ポインター型に割り当てようとしたことを検出します。たとえば、32 ビット `int` または `long` を 64 ビット ポインターにキャストした場合などです。

この変換は、符号拡張が発生する場合、32 ビットに収まるポインター値であっても安全でないことがあります。 負の 32 ビット整数が 64 ビット ポインター型に割り当てられる場合、符号拡張によって、ポインター値が整数の値とは異なるメモリ アドレスを参照するようになります。

この警告は、64 ビット コンパイル ターゲットに対してのみ発行されます。 詳細については、「[ポインターを使用するための規則](/windows/win32/WinProg64/rules-for-using-pointers)」を参照してください。

次のコード例は、64 ビットのターゲットのコンパイル時に C4312 を生成します。

```
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```