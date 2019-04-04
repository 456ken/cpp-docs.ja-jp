---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: 42adff6564dc1c2ef47abffe9f9e6e630279ea7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812461"
---
# <a name="qspectre"></a>/Qspectre

Spectre バリアント 1 セキュリティの脆弱性を軽減するための手順のコンパイラ生成を指定します。

## <a name="syntax"></a>構文

> **/Qspectre**

## <a name="remarks"></a>Remarks

**/Qspectre**オプションは、Visual Studio 2017 バージョン 15.5.5 で使用できる以降、および使用の Visual Studio 2015 Update 3 で[KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre)します。 特定の操作を軽減するために手順を挿入するコンパイラが、その[Spectre セキュリティの脆弱性](https://spectreattack.com/spectre.pdf)します。 これらの脆弱性と呼ばれる*予測実行のサイド チャネル攻撃*に影響する多くのオペレーティング システムと最新のプロセッサ、AMD、intel プロセッサを含む、および ARM です。

**/Qspectre**オプションは既定でオフです。

最初のリリースで、 **/Qspectre**最適化されたコードをオプションでのみ機能します。 Visual Studio 2017 バージョン 15.7 以降で、 **/Qspectre**オプションがすべての最適化レベルでサポートされています。

Microsoft Visual C ライブラリでは、Spectre の軽減策のバージョンで入手できます。 Visual Studio 2017 の Spectre 軽減ライブラリは、Visual Studio インストーラーでダウンロードできます。 内にある、**個々 のコンポーネント**タブ**コンパイラ、ビルド ツール、およびランタイム**、"Spectre 用ライブラリ"を名前であるとします。 DLL と軽減策を有効になっているスタティック ランタイム ライブラリの両方には、利用できる Visual C ランタイムのサブセットです。VC + + のスタートアップ コード、vcruntime140、msvcp140、concrt140、および vcamp140 します。 Dll はアプリケーションのローカル展開だけです。Visual C 2017 ランタイム ライブラリ Redistributable の内容が変更されていません。 MFC と ATL で見つかった Spectre 軽減ライブラリをインストールすることも、**個々 のコンポーネント**タブ**Sdk、ライブラリ、およびフレームワーク**します。

### <a name="applicability"></a>適用性

信頼境界を越えるデータ、コードを操作し、使用することをお勧めします。 場合、 **/Qspectre**を再構築し、できるだけ早くこの問題を軽減するために、コードを再デプロイするにはオプションです。 などを使用してリモート プロシージャ コードを呼び出す信頼できない入力ファイルやファイルを解析または他の間でローカルのプロセスを使用して、信頼境界を越えるデータを操作するコードの例には実行に影響を与える信頼できない入力を読み込むコードが含まれます通信 (IPC) インターフェイス。 サンド ボックス化の標準的な手法は十分でない可能性があります。 コードが信頼境界を越えないことを決定する前に、サンド ボックスを注意深く調べる必要があります。

### <a name="availability"></a>可用性

**/Qspectre**オプションは Visual Studio 2017 バージョン 15.5.5 では、2018 年 1 月 23 日以降に行われたすべての更新を Microsoft の MSVC コンパイラ (MSVC) で使用できます。 Visual Studio インストーラーを使用して、個々 のコンポーネントとして、Spectre 軽減ライブラリをインストールして、コンパイラを更新します。 **/Qspectre**オプションも Visual Studio 2015 Update 3 で修正プログラムを利用します。 詳細については、[KB 4338871](https://support.microsoft.com/help/4338871)を参照してください。

15.5 とすべてのプレビューの Visual Studio 2017 バージョン 15.6 では、文書化されていないオプションでは、Visual Studio 2017 バージョンのすべてのバージョン **/d2guardspecload**、つまりと同等の初期動作 **/Qspectre**. 使用することができます **/d2guardspecload**これらのバージョンのコンパイラでは、コードに同じの軽減策を適用します。 使用するようにビルドを更新してください。 **/Qspectre** ; オプションをサポートするためのコンパイラで、 **/Qspectre**オプションは新しい軽減策を以降のバージョンのコンパイラでサポートも可能性があります。

### <a name="effect"></a>効果

**/Qspectre**オプション亡霊バリアント 1、境界チェックのバイパスを軽減するためにコードを出力する[CVE 2017-5753 に対する](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)します。 投機的なコード実行のバリアとして機能する命令の挿入することによって動作します。 プロセッサ投機を軽減するために使用される特定の手順では、プロセッサとそのマイクロ アーキテクチャに依存およびの将来のバージョンのコンパイラで変更される可能性です。

ときに、 **/Qspectre**オプションが有効になっている、コンパイラは予測実行が範囲チェックが無視され、バリアの命令を挿入のインスタンスを識別しようとしています。 コンパイラは、バリアント 1 のインスタンスを識別するために実行できる分析に制限があることに注意してください。 重要です。 そのため、バリアント 1 のすべての可能なインスタンスが インストルメント化される保証はありません **/Qspectre**します。

### <a name="performance-impact"></a>パフォーマンスに与える影響

パフォーマンスに与える影響 **/Qspectre**いくつかの非常に大きなコード ベースで無視できること確認されていますが、保証はありません コードのパフォーマンスに影響を **/Qspectre**でも影響を受けません。 パフォーマンス オプションの効果を決定するコードのベンチマークを実行する必要があります。 使用して、軽減策を選択的に無効にパフォーマンスが重要なブロックまたはループ、軽減策が必要ないことがわかっている場合、 [__declspec(spectre(nomitigation))](../../cpp/spectre.md)ディレクティブ。 このディレクティブはのみをサポートするためのコンパイラで使用できません、 **/d2guardspecload**オプション。

### <a name="required-libraries"></a>必要なライブラリ

**/Qspectre**コンパイラ オプションは、暗黙的に組み込まれている Spectre の軽減策を提供するランタイム ライブラリのバージョンをリンクするコードを生成します。 これらのライブラリは、省略可能なコンポーネント、Visual Studio インストーラーを使用してインストールする必要があります。

- Vc++ 2017 バージョン*version_numbers* Spectre 用ライブラリ\[(x86 および x64) |(ARM) |(ARM64)]
- 用の visual C ATL \[(x86 または x64) |ARM |ARM64] Spectre の軽減策
- 用の visual C MFC \[x86 または x64 |ARM |ARM64] Spectre の軽減策

使用して、コードをビルドする場合 **/Qspectre**おり、これらのライブラリがないビルド システム レポートをインストールします。**警告 msb 8038。Spectre の軽減策が有効になっているが、Spectre 軽減ライブラリが見つかりません**します。 場合は、MFC または ATL コードのビルドに失敗して、リンカーなどのエラーのレポート**致命的なエラー LNK1104: ファイル 'oldnames.lib' を開くことができません**、これらの不足しているライブラリが原因になる可能性があります。

### <a name="additional-information"></a>追加情報

詳細については、公式ページをご覧ください[予測実行のサイド チャネルの脆弱性を軽減するには、Microsoft セキュリティ アドバイザリ ADV180002、ガイダンス](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)します。 ガイダンスは、Intel から入手できるも[投機実行サイド チャネルの軽減策](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)、および ARM、[キャッシュ推理のサイド チャネル](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)します。 Spectre や Meltdown の軽減策の特定の Windows の概要については、次を参照してください。[の Windows システムで Spectre や Meltdown の軽減策のパフォーマンスに与える影響を理解する](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)Microsoft セキュリティで保護されたブログ。 MSVC の軽減策が指す Spectre 脆弱性の概要については、[MSVC の、Spectre の軽減策](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./)Visual c チーム ブログにを参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)を参照してください。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 入力、 **/Qspectre**コンパイラ オプションで、**追加オプション**ボックス。 選択**OK**して変更を適用します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](q-options-low-level-operations.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンドラインの構文](compiler-command-line-syntax.md)
