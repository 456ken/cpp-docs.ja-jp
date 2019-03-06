---
title: インポートのバインド
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 90af3af7e71928b18c77c0d21ff6a30c4561e251
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415241"
---
# <a name="binding-imports"></a>インポートのバインド

既定のリンカーの動作では、遅延読み込み DLL のバインド可能なインポート アドレス テーブルを作成します。 ヘルパー関数が呼び出す代わりに、バインドされた情報を使用しようとして、DLL がバインドされている場合**GetProcAddress**各参照されているインポートします。 タイムスタンプまたは優先アドレスが一致しないものと、読み込まれた DLL の場合、ヘルパー関数は、バインドされたインポート アドレス テーブルが古くなっていると、存在しないかのように続行されますと想定されます。

DLL の遅延読み込みしたインポートをバインドしない場合に指定する[/delay](../../build/reference/delay-delay-load-import-settings.md): リンカーのコマンドラインでは、イメージ ファイルの生成および使用領域の中からバインドされたインポート アドレス テーブルを防止します。

## <a name="see-also"></a>関連項目

[リンカーによる DLL の遅延読み込み](../../build/reference/linker-support-for-delay-loaded-dlls.md)
