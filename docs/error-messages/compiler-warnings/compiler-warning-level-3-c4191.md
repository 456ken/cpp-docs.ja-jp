---
title: コンパイラの警告 (レベル 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: 72a485811647911207b6d048c686acdadd142b65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402256"
---
# <a name="compiler-warning-level-3-c4191"></a>コンパイラの警告 (レベル 3) C4191

'operator/operation' : 'type of expression' から 'type required' への変換は保証されません

関数ポインターを使用するいくつかの操作は安全でないと見なされます。

- 関数の種類の呼び出し規則が異なる場合。

- 関数の種類の復帰規則が異なる場合。

- 引数または戻り値の型のサイズ、型のカテゴリ、または分類が異なる場合。

- 引数リストの長さが異なる場合 ( `__cdecl`では、短い方の引数リストが varargs であっても、長い方のリストから短い方へキャストされる場合のみ)。

- データへのポインター (以外の**void**<strong>\*</strong>) 関数へのポインターに対してエイリアス。

- その他の型の違いによって、 `reinterpret_cast`でエラーまたは警告が発生する場合。

結果として得られたポインターを使用して関数を呼び出すと、プログラムがクラッシュする可能性があります。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では C4191 が生成されます。

```
// C4191.cpp
// compile with: /W3 /clr
#pragma warning(default: 4191)

void __clrcall f1() { }
void __cdecl   f2() { }

typedef void (__clrcall * fnptr1)();
typedef void (__cdecl   * fnptr2)();

int main() {
   fnptr1 fp1 = static_cast<fnptr1>(&f1);
   fnptr2 fp2 = (fnptr2) &f2;

   fnptr1 fp3 = (fnptr1) &f2;   // C4191
   fnptr2 fp4 = (fnptr2) &f1;   // C4191
};
```