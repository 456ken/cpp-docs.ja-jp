---
title: /WX (リンカー警告をエラーとして扱う)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: fa7b651d2a884e25a9b0e6f1ba824d082c3c01bc
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412647"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (リンカー警告をエラーとして扱う)

```
/WX[:NO]
```

## <a name="remarks"></a>Remarks

/WX には、リンカーが警告を生成する場合に生成される出力ファイルは行われません。

似ています **/WX**コンパイラ (を参照してください[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、//we、/wo、/Wv、/WX (警告レベル)](../../build/reference/compiler-option-warning-level.md)詳細については)。 ただしを指定する **/WX**のコンパイルとは限りませんが **/WX**リンク フェーズが無効にも、明示的に指定する必要があります。 **/WX**ツールごとにします。

既定では、 **/WX**は無効です。 リンカー警告をエラーとして扱う、次のように指定します。 **/WX**します。 **/WX:NO**は指定しない場合と同じ **/WX**します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. オプションを入力、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)
