---
title: /analyze (コード分析)
ms.date: 10/15/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: f537fdea2703805c7ab1c57ba0d4429f6b683ae4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444889"
---
# <a name="analyze-code-analysis"></a>/analyze (コード分析)

コード分析とコントロール オプションを有効にします。

## <a name="syntax"></a>構文

> **/analyze**-] **[: WX-]** [ **: log** *filename*] **[: quiet]** [:**stacksize** *number*] [:**max_paths** *number*] **[: only]** [ **: ルールセット***ルール*] [ **:p lugin***プラグイン-dll*]

## <a name="arguments"></a>引数

**/analyze**\
既定のモードで分析をオンにします。 分析出力は、他のエラーメッセージと同様に**出力**ウィンドウに移動します。 分析を明示的にオフにするには **、/analyze e-** を使用します。

**/analyze: WX-** \
**/Wx**を使用してコンパイルする場合、コード分析の警告はエラーとして扱われません。 詳細については、「 [/wx (警告レベル)](compiler-option-warning-level.md)」を参照してください。

**/analyze: ログ***ファイル名*\
詳細なアナライザーの結果は、 *filename*によって指定されたファイルに XML として書き込まれます。

**/analyze: quiet**\
アナライザーの出力が**出力**ウィンドウに表示されないようにします。

**/analyze: stacksize** *番号*\
このオプションと共に使用する*number*パラメーターでは、警告[C6262](/visualstudio/code-quality/c6262)が生成されるスタックフレームのサイズ (バイト単位) を指定します。 *数値*の前のスペースは省略可能です。 このパラメーターが指定されていない場合、スタックフレームサイズは既定で 16 KB になります。

**/analyze: max_paths** *番号*\
このオプションで使用される*number*パラメーターでは、分析するコードパスの最大数を指定します。 このパラメーターが指定されていない場合、既定では、数値は256です。 値を大きくすると、より詳細なチェックが行われますが、分析に時間がかかることがあります。

**/analyze:** \ のみ
通常、コンパイラは、アナライザーを実行した後にコードを生成し、構文チェックをさらに実行します。 **/Analyze: only**オプションは、このコード生成パスをオフにします。 これにより、分析が高速になりますが、コンパイラのコード生成パスが生成されない可能性があるエラーと警告がコンパイルされます。 プログラムにコード生成エラーがない場合は、分析結果が信頼できない可能性があります。 このオプションを使用することをお勧めするのは、コードがエラーなしでコード生成構文チェックに合格した場合のみです。

**/analyze: ルールセット** *file_path*\
自分で作成できるカスタム規則セットなど、分析する規則セットを指定できます。 このスイッチを設定すると、ルールエンジンは、実行前に指定された規則セットの非メンバーを除外するため、より効率的になります。 それ以外の場合、エンジンはすべてのルールを確認します。

Visual Studio に付属しているルールセットは、%VSINSTALLDIR%\Team ツールの *静的な分析ツール \ ルールセットの設定*に含まれています。

次のサンプルカスタムルールセットは、C6001 と C26494 をチェックするようにルールエンジンに指示します。 このファイルは、@no__t 0 の拡張子が付いている限り、任意の場所に配置できます。引数に完全なパスを指定します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

**/analyze: plugin** *plugin*\
コード分析の実行の一部として、指定された PREfast プラグインを有効にします。

::: moniker range="<=vs-2017"

LocalC261XX は、同時実行に関連するコード分析チェックを実装するプラグインです。 たとえば、 [C26100](/visualstudio/code-quality/c26100)、 [C26101](/visualstudio/code-quality/c26101)、 [C26167](/visualstudio/code-quality/c26167)のようになります。

Local、c .dll を実行するには、次のコンパイラオプションを使用します。 **/analyze: Plugin Localて c .dll**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck は、C261XX 警告の範囲内で同時実行に関連するコード分析チェックを実装します。 たとえば、 [C26100](/visualstudio/code-quality/c26100)、 [C26101](/visualstudio/code-quality/c26101)、 [C26167](/visualstudio/code-quality/c26167)のようになります。

ConcurrencyCheck を実行するには、まず開発者コマンドプロンプトから次のコマンドを実行します。

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

その後、次のコンパイラオプションを使用します。 **/analyze: プラグイン**では、dll を使用します。

::: moniker-end

CppCoreCheck を実行するには、まず開発者コマンドプロンプトから次のコマンドを実行します。

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

その後、次のコンパイラオプションを使用します。 **/analyze: プラグイン**では、dll を使用します。

## <a name="remarks"></a>Remarks

詳細については、「 [c/C++ ](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) c + + のコード分析」と「 [c/C++警告のコード分析](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)」を参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. **構成プロパティ** > **コード分析** > **全般**プロパティページを選択します。

1. 1つ以上の**コード分析**プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
