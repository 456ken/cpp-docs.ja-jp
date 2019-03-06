---
title: /LARGEADDRESSAWARE (大きいアドレスの処理)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 9ea26a87ce85f71188ca77345e4af055d3ffbf0e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413746"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (大きいアドレスの処理)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Remarks

/LARGEADDRESSAWARE オプションは、アプリケーションが、2 ギガバイトを超えるアドレスを処理できることをリンカーに指示します。 64 ビットのコンパイラでは、このオプションは既定で有効にします。 32 ビットのコンパイラでは、リンカーのコマンドラインで/LARGEADDRESSAWARE が指定されない場合/LARGEADDRESSAWARE:NO が有効にします。

アプリケーションの/LARGEADDRESSAWARE、DUMPBIN は関連付け[/HEADERS](../../build/reference/headers.md)それに対応する情報が表示されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**システム**プロパティ ページ。

1. 変更、**大きいサイズのアドレスを有効にする**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)
