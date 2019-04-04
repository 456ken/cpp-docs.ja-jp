---
title: コンパイラ エラー C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: c73a8d4fcde945ddf2495cc2d0d7dc47216f2db3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587591"
---
# <a name="compiler-error-c2434"></a>コンパイラ エラー C2434

> '*シンボル*': __declspec(process) と共に宣言されたシンボルは/clr で動的に初期化できません: ピュア モード

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

プロセスごとの変数を動的に初期化することはできません **/clr: 純粋な**します。 詳細については、[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)と[プロセス](../../cpp/process.md)を参照してください。

## <a name="example"></a>例

次の例では、C2434 が生成されます。 この問題を解決するには、初期化するために定数を使用`process`変数。

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```