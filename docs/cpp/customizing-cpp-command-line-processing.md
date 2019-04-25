---
title: C++ コマンド ライン処理のカスタマイズ
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: da1b3bdd6392b144f9315add4c19de14c1d14d41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154692"
---
# <a name="customizing-c-command-line-processing"></a>C++ コマンド ライン処理のカスタマイズ

## <a name="microsoft-specific"></a>Microsoft 固有の仕様

プログラムがコマンド ラインの引数を受け取らない場合は、コマンド ライン処理を実行するライブラリ ルーチンの使用を制約することで、領域を節約できます。 このルーチンを呼び出す`_setargv`しで説明されているが[ワイルドカードの展開](../cpp/wildcard-expansion.md)します。 使用を抑制するには、含んでいるファイルで何も実行しないルーチンを定義、`main`関数、および名前を付けます`_setargv`します。 呼び出し`_setargv`の定義によって満たされる`_setargv`ライブラリのバージョンは読み込まれません。

同様に、使用して環境テーブルにアクセスしない場合、`envp`引数の代わりに使用する独自の空ルーチンを提供できます`_setenvp`、環境処理ルーチン。 同様、`_setargv`関数、`_setenvp`として宣言する必要があります**extern"C"** します。

プログラムは、呼び出しを行うことがあります、`spawn`または`exec`C ランタイム ライブラリ ルーチンのファミリです。 この場合、このルーチンは親プロセスから子プロセスに環境を渡すために使用されるため、環境処理ルーチンを抑制しないでください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[main:プログラムの起動](../cpp/main-program-startup.md)