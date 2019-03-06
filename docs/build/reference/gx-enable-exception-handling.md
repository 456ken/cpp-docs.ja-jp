---
title: /GX (例外処理の有効化)
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 4ac2b86c19845a092c743c484ad48d0cd0b6fb35
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416034"
---
# <a name="gx-enable-exception-handling"></a>/GX (例外処理の有効化)

非推奨。 使用して宣言された関数であるという前提を使用して同期例外処理できるように`extern "C"`例外はスローされません。

## <a name="syntax"></a>構文

```
/GX
```

## <a name="remarks"></a>Remarks

**/GX**は非推奨とされます。 相当するものを使用して、 [/EHsc](../../build/reference/eh-exception-handling-model.md)オプションを使用します。 非推奨のコンパイラ オプションの一覧は、次を参照してください。、**非推奨とされた削除済みのコンパイラ オプション**セクション[Compiler Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md)します。

既定では、 **/EHsc**と等価の **/GX**、Visual Studio 開発環境を使用してコンパイルする場合は適用されます。 コマンド ライン ツールを使用すると例外処理を指定しません。 これは、相当の**では/GX-** します。

詳細については、次を参照してください。 [C++ 例外処理](../../cpp/cpp-exception-handling.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. ナビゲーション ウィンドウで、**構成プロパティ**、 **C/C++**、**コマンドライン**します。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)<br/>
[/EH (例外処理モデル)](../../build/reference/eh-exception-handling-model.md)
