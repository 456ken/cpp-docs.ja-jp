---
title: /GZ (スタック フレームのランタイム エラー チェックの有効化)
ms.date: 11/04/2016
f1_keywords:
- /gz
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
ms.openlocfilehash: 35475b87b8f59fbb0fb24e62690f8fc24c7cb4e9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423470"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (スタック フレームのランタイム エラー チェックの有効化)

同じ操作を実行、 [/RTC (ランタイム エラー チェック)](../../build/reference/rtc-run-time-error-checks.md)オプション。 非推奨。

## <a name="syntax"></a>構文

```
/GZ
```

## <a name="remarks"></a>Remarks

**/GZ**のみで使用するよう強制されます ([/Od (無効 (デバッグ))](../../build/reference/od-disable-debug.md)) を構築します。

**/GZ**は Visual Studio 2005; 非推奨を使用して、 [/RTC (ランタイム エラー チェック)](../../build/reference/rtc-run-time-error-checks.md)代わりにします。 非推奨のコンパイラ オプションの一覧は、次を参照してください。**非推奨とされた削除済みのコンパイラ オプション**で[Compiler Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)
