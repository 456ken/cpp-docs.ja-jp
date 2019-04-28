---
title: /ZW (Windows ランタイムのコンパイル)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: 73295866004fd506fd5f06ff25c048d14b821016
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315314"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Windows ランタイムのコンパイル)

ソース Visual C コンポーネント拡張 C + をサポートするためにコードをコンパイル/cli CX のユニバーサル Windows プラットフォーム (UWP) アプリを作成するためです。

使用すると **/ZW**をコンパイルするには、常に指定 **/EHsc**もします。

## <a name="syntax"></a>構文

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>引数

**nostdlib**<br/>
Platform.winmd、Windows.Foundation.winmd、および他の既定の Windows メタデータ (.winmd) ファイルがコンパイルで自動に含まれていないことを示します。 代わりに、使用する必要があります、 [/FU (Name Forced #using ファイルの using)](fu-name-forced-hash-using-file.md) Windows メタデータ ファイルを明示的に指定するコンパイラ オプション。

## <a name="remarks"></a>Remarks

指定した場合、 **/ZW**オプション、コンパイラは、これらの機能をサポートしています。

- 必要なメタデータ ファイル、名前空間、データ型、および Windows ランタイムで実行するアプリを必要とする関数。

- 自動で Windows ランタイム オブジェクトの参照カウントと自動参照カウントがゼロになったときに、オブジェクトの破棄します。

Incremental linker を使用して、.obj ファイルに含まれる Windows メタデータをサポートしていないため、 **/ZW**オプション、非推奨とされる[/Gm (簡易リビルドの有効)](gm-enable-minimal-rebuild.md)オプションはと互換性がない **/ZW**します。

詳細については、次を参照してください。 [Visual c 言語リファレンス](../../cppcx/visual-c-language-reference-c-cx.md)します。

## <a name="requirements"></a>必要条件

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
