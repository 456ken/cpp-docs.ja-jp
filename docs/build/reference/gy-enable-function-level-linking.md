---
title: /Gy (関数レベルのリンクの有効化)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 368bd469a303222ef4d5177677de4940e402b6de
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413109"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (関数レベルのリンクの有効化)

コンパイラが個々の関数をパッケージ関数 (COMDAT) の形式でパッケージ化できるようになります。

## <a name="syntax"></a>構文

```
/Gy[-]
```

## <a name="remarks"></a>Remarks

リンカーは、関数が、除外したり、DLL、または .exe ファイルで個別の関数の順序の Comdat として個別にパッケージ化することが必要です。

リンカー オプションを使用する[/OPT (最適化)](../../build/reference/opt-optimizations.md) .exe ファイルから参照されていないパッケージ化された関数を除外します。

リンカー オプションを使用する[/ORDER (順序で配置関数)](../../build/reference/order-put-functions-in-order.md)に .exe ファイルで指定した順序でパッケージ化された関数を含めます。

インライン関数は、インスタンスが呼び出される場合に常にパッケージ化されます (が発生する、たとえば、インライン化がオフまたは関数のアドレスを取得する)。 さらに、クラス宣言で定義されている C++ メンバー関数は自動的にパッケージ化されます。その他の関数は使用されませんし、それらをパッケージ化された関数としてコンパイルする必要はこのオプションを選択します。

> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 、エディット コンティニュを使用するオプションが自動的に設定、 **/Gy**オプション。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**コード生成**プロパティ ページ。

1. 変更、**関数レベルのリンクを有効にする**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)
