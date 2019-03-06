---
title: /OUT (出力ファイル名)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: 395a2475ec572476f80b17cc5ffab7c2724e6b02
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418049"
---
# <a name="out-output-file-name"></a>/OUT (出力ファイル名)

```
/OUT:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
ユーザーが指定した出力ファイルの名前。 既定の名前が置き換えられます。

## <a name="remarks"></a>Remarks

/OUT オプションには、既定の名前と、リンカーによって作成されるプログラムの場所がオーバーライドされます。

既定では、リンカーは、最初に指定された .obj ファイル (.exe または .dll) には、適切な拡張機能のベース名を使用して、ファイル名を形成します。

これは、オプションはマップまたはインポート ライブラリの既定の基本名。 詳細については、次を参照してください。[マップ ファイルの生成](../../build/reference/map-generate-mapfile.md)(/map) と[/IMPLIB](../../build/reference/implib-name-import-library.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**全般**プロパティ ページ。

1. 変更、**出力ファイル**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)
