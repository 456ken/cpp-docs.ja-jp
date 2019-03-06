---
title: BSCMAKE コマンド ライン
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: b6268eb6d0ea39e72a1d8fd40ab563347c05f0c6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416840"
---
# <a name="bscmake-command-line"></a>BSCMAKE コマンド ライン

BSCMAKE を実行するには、次のコマンドライン構文を使用します。

```
BSCMAKE [options] sbrfiles
```

オプションでのみ表示されます、`options`コマンドラインでフィールド。

*Sbrfiles*フィールドは、コンパイラまたはアセンブラーによって作成された 1 つ以上の .sbr ファイルを指定します。 スペースまたはタブでは、.sbr ファイルの名前を区切ります。 拡張子を指定する必要があります。既定値はありません。 ファイル名は、パスを指定して、オペレーティング システムのワイルドカードを使用することができます (\*と?)。

インクリメンタル ビルドでは、最初のビルドに含まれていない新しい .sbr ファイルを指定できます。 すべての貢献をブラウザー情報ファイルに保持する場合は、.bsc ファイルの作成に使用された最初 (切り捨てられたファイルを含む) すべての .sbr ファイルを指定する必要があります。 .Sbr ファイルを省略した場合は、ブラウザー情報ファイルをそのファイルの貢献度が削除されます。

フル ビルドの切り捨てられた .sbr ファイルを指定しません。 完全なビルドでは、すべての指定した .sbr ファイルからの投稿が必要です。 フル ビルドを実行する前に、プロジェクトを再コンパイルし、空のファイルごとに新しい .sbr ファイルを作成します。

次のコマンドは、3 つの .sbr ファイルから MAIN.bsc をという名前のファイルをビルドするにを実行します。

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

関連情報については、次を参照してください。 [BSCMAKE コマンド ファイル](../../build/reference/bscmake-command-file-response-file.md)と[BSCMAKE オプション](../../build/reference/bscmake-options.md)します。

## <a name="see-also"></a>関連項目

[BSCMAKE リファレンス](../../build/reference/bscmake-reference.md)
