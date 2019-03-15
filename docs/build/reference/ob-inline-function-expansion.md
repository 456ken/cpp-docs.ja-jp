---
title: /Ob (関数のインライン展開)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 6bf16e5725916e81e64d80c0a1f96bf502c8826c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807500"
---
# <a name="ob-inline-function-expansion"></a>/Ob (関数のインライン展開)

関数のインライン展開を制御します。

## <a name="syntax"></a>構文

> /Ob {0 | 1 | 2}

## <a name="arguments"></a>引数

**0**<br/>
インライン展開を無効にします。 既定では、コンパイラの裁量で、すべての機能拡張が発生したとも呼ば*自動インライン展開*します。

**1**<br/>
マークされた関数ののみ拡張できます[インライン](../../cpp/inline-functions-cpp.md)、 `__inline`、または`__forceinline`、またはクラス宣言で定義されている C++ メンバー関数。

**2**<br/>
既定値。 
  `inline`、`__inline`、または `__forceinline` としてマークされた関数の展開、およびコンパイラが選択するその他すべての関数が許可されます。

**/Ob2**ときは、 [/O1、/O2 (サイズの最小化、速度の最大化)](o1-o2-minimize-size-maximize-speed.md)または[/Ox (有効にする最もの速度の最適化)](ox-full-optimization.md)使用されます。

このオプションを使用して最適化を有効にする必要があります **/O1**、 **/O2**、 **/Ox**、または **/Og**します。

## <a name="remarks"></a>Remarks

インライン展開に関するオプションとキーワードは、インライン展開の対象となる候補をコンパイラに示すだけです。 すべての関数がインライン展開になるという保証はありません。 インライン展開は無効にすることができますが、`__forceinline` キーワードを使用しても、特定の関数のインライン展開をコンパイラに強制することはできません。

使用することができます、 `#pragma` [auto_inline](../../preprocessor/auto-inline.md)関数をインライン展開の候補として考慮の対象から除外するディレクティブ。 また、 `#pragma` [組み込み](../../preprocessor/intrinsic.md)ディレクティブ。

> [!NOTE]
> プロファイリングのテスト実行から収集される情報にはそれ以外の場合に効果を指定する場合の最適化よりも優先されます **/Ob**、 **/Os**、または **/Ot**します。 詳細については、次を参照してください。[ガイド付き最適化の](../profile-guided-optimizations.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 展開**構成プロパティ**、 **C/C++**、選択と**最適化**します。

1. 変更、**関数のインライン展開**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>

## <a name="see-also"></a>関連項目

[/O オプション (コードの最適化)](o-options-optimize-code.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンドラインの構文](compiler-command-line-syntax.md)
