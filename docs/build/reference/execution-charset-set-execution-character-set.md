---
title: /execution-charset (実行文字セット)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 14d6cf5e6f1982cb3079093294770f4d78faa478
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422456"
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset (実行文字セット)

実行文字セットの実行可能ファイルで指定できます。

## <a name="syntax"></a>構文

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引数

*IANA_name*<br/>
IANA で定義されている文字セットの名前。

*CPID*<br/>
コード ページ id。

## <a name="remarks"></a>Remarks

使用することができます、 **/execution-charset**実行文字セットを指定するオプション。 実行文字セットは、すべての前処理ステップ コンパイル フェーズに入力されるプログラムのテキストに使用されるエンコーディングします。 この文字セットは、コンパイルされたコード内の文字列または文字リテラルの内部表現に使用されます。 ソース ファイルがない基本実行文字セットで表現できる文字を含めるときに使用する拡張実行文字セットを指定するには、このオプションを設定します。 IANA のいずれかを使用する ISO 文字セットの名前、またはドット (.) の後に使用する文字セットを指定する 3 ~ 5 桁の 10 進コード ページ識別子。 一覧には、コード ページ識別子がサポートされている文字セットの名前を参照してください。[コード ページ識別子](/windows/desktop/Intl/code-page-identifiers)します。

既定では、Visual Studio は、utf-8 または utf-16、たとえば、ソース ファイルが、エンコードされた Unicode 形式であるか判断のバイト順マークを検出します。 バイト順マークが見つからない場合は、ソース ファイルを使ってエンコードされるユーザーの現在のコード ページで、文字を使用して名前またはコード ページの設定を指定していない限り想定しています、 **/source-charset**オプションまたは **/utf-8。** オプション。 Visual Studio では、いくつかの文字エン コードのいずれかを使用して、C++ ソース コードを保存できます。 ソースと実行文字セットの詳細については、次を参照してください。[文字セット](../../cpp/character-sets.md)言語ドキュメント。

使用することができます、ソース文字セットと、実行文字セットの両方を utf-8 に設定する場合、 **/utf-8**ショートカットとしてコンパイラ オプション。 指定することと同じである **/source -charset:utf-8/execution-charset:utf-8**コマンド行にします。 これらのいずれかのオプションも有効、 **/validate-charset**既定ではオプションです。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクト プロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 展開、**構成プロパティ**、 **C/C++**、**コマンドライン**フォルダー。

1. **追加オプション**、追加、 **/execution-charset**オプション、および、使用するエンコーディングを指定します。

1. **OK** を選択して変更を保存してください。

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)<br/>
[/source-charset (ソース文字セットの設定)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8 (ソースと実行可能ファイルの文字セットを UTF-8 に設定する)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (互換性のある文字の検証)](../../build/reference/validate-charset-validate-for-compatible-characters.md)
