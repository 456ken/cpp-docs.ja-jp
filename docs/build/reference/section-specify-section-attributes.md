---
title: /SECTION (セクション属性の指定)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 8fb73043c9c185adee0859bb81098eab022430c2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816556"
---
# <a name="section-specify-section-attributes"></a>/SECTION (セクション属性の指定)

> **/SECTION:**_name_,**[!]**{**DEKPRSW**}][**,ALIGN=**_number_]

## <a name="remarks"></a>Remarks

**/Section**オプションは、属性は、セクションの .obj ファイルがコンパイルされたときの設定をオーバーライドするセクションの属性を変更します。

A*セクション*ポータブル実行可能 (PE) ファイルがコードまたはデータを含むメモリの連続する名前付きブロック。 いくつかのセクションには、コードまたはプログラムが宣言され、データのセクションでは他のリンカーと (lib.exe) ライブラリ マネージャーを作成し、オペレーティング システムに不可欠な情報が含まれてときに、直接使用するデータが含まれます。 詳細については、[PE 形式](/windows/desktop/Debug/pe-format)を参照してください。

コロン (:) とセクション指定*名前*します。 *名前*は大文字小文字を区別します。

標準の名前と競合すると、次の名前を使わないでください。 たとえば、.sdata は RISC プラットフォームで使用します。

- .arch

- .bss

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

セクションの 1 つまたは複数の属性を指定します。 次に、属性文字は、大文字小文字が区別ではありません。 セクションに必要とするすべての属性を指定する必要があります。省略された属性の文字は、その属性のビットをオフにします。 R や W、E、既存の読み取り、書き込み、指定しない場合は実行可能ファイルの状態は変更されません。

属性を否定するには、前に感嘆符 (!) には、その文字を付けます。 属性の文字の意味は次の表に示します。

|文字|属性|説明|
|---------------|---------------|-------------|
|E|実行|セクションが実行可能ファイル|
|R|読み取り|データの読み取り操作します。|
|W|Write|データの書き込み操作します。|
|S|Shared|イメージを読み込むすべてのプロセス間でセクションを共有します|
|D|破棄できます。|破棄可能セクションをマークします。|
|K|キャッシュ可能|セクションをキャッシュ不可としてマークします。|
|P|ページング可能|セクションをページング不可としてマークします。|

K および P は、それらに対応するセクションのフラグが負の値の意味で使用されるということ、通常します。 かどうか 1 つ .text セクションで使用して指定する、 **/SECTION:.text, K**オプションで実行すると、セクション フラグに違いはありません、 [DUMPBIN](dumpbin-options.md)で、 [/HEADERS](headers.md)オプション。セクションが暗黙的に既にキャッシュされました。 既定値を削除する指定 **/SECTION:.text、!K**代わりにします。 DUMPBIN には、「キャッシュされません」などのセクションの特性が表示されます。

電子メール、R、または W の設定を持たない PE ファイルのセクションでは、おそらく無効です。

**ALIGN =**_数_引数では、特定のセクションのアラインメント値を指定することができます。 _数_引数をバイト単位で、2 の累乗である必要があります。 参照してください[/align](align-section-alignment.md)詳細についてはします。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)を参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. オプションを入力して、**追加オプション**ボックス。 選択**OK**または**適用**して変更を適用します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーの参照](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
