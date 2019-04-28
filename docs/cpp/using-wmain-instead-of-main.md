---
title: main に代わる wmain の使用
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: 8cdc986d1582d2b26f137e3147ce78bc83e9daca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257973"
---
# <a name="using-wmain-instead-of-main"></a>main に代わる wmain の使用

## <a name="microsoft-specific"></a>Microsoft 固有の仕様

Unicode プログラミング モデルでのワイド文字バージョンを定義することができます、`main`関数。 使用**wmain**の代わりに`main`Unicode 仕様に準拠した移植可能なコードを記述する場合。

仮パラメーターを宣言する**wmain**に同様の形式を使用して`main`します。 さらに、ワイド文字の引数と、必要であればワイド文字環境ポインターもプログラムに渡すことができます。 *Argv*と*envp*パラメーター **wmain**型`wchar_t*`します。

プログラムで使用する場合、`main`関数の場合、マルチバイト文字環境はプログラムの起動時にオペレーティング システムによって作成します。 必要な場合にのみ、環境のワイド文字のコピーが作成されます (などを呼び出して、 [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)または[_wputenv](../c-runtime-library/reference/putenv-wputenv.md)関数)。 `_wputenv` を最初に呼び出すとき、または MBCS 環境が既に存在する場合に `_wgetenv` を最初に呼び出すとき、対応するワイド文字列環境が作成され、その後は作成されたワイド文字列環境が `_wenviron` グローバル変数 (`_environ` グローバル変数のワイド文字バージョン) によって参照されます。 この時点までで、2 つの環境のコピー (MBCS および Unicode) が同時に存在していることになるわけですが、両方ともプログラムが消滅するまでオペレーティング システムによって保持されます。

同様に、プログラムで使用する場合、 **wmain**関数、MBCS (ASCII) 環境を作成する最初の呼び出しで`_putenv`または`getenv`が指すと、`_environ`グローバル変数。

MBCS 環境の詳細については、次を参照してください。[シングル バイト文字とマルチバイト文字セット](../c-runtime-library/single-byte-and-multibyte-character-sets.md)で、*ランタイム ライブラリのリファレンス。*

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[main:プログラムの起動](../cpp/main-program-startup.md)