---
title: MFC DLL プロジェクトの作成
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 21173582f68b1d50fefbe22250546fcce63730b4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278835"
---
# <a name="creating-an-mfc-dll-project"></a>MFC DLL プロジェクトの作成

MFC DLL とは、複数のアプリケーションで同時に利用できる関数の共有ライブラリとして機能する、バイナリ ファイルです。 MFC DLL プロジェクトを作成する最も簡単な方法は、MFC DLL ウィザードを使用する方法です。

> [!NOTE]
>  IDE に表示される機能は、有効にされている設定やエディションに依存し、ヘルプに記載されている内容とは異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>MFC DLL ウィザードを使用して MFC DLL プロジェクトを作成するには

1. ヘルプ トピックの「[アプリケーション ウィザードを使用したデスクトップ プロジェクトの作成](../../ide/creating-desktop-projects-by-using-application-wizards.md)」の手順に従います。

**注**で、**新しいプロジェクト**ダイアログ ボックスで、 `MFC DLL` MFC DLL ウィザードを開く [テンプレート] ペインでアイコン。

1. 使用して、アプリケーションの設定を定義、[アプリケーション設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)のページ、 [MFC DLL ウィザード](../../mfc/reference/mfc-dll-wizard.md)します。

    > [!NOTE]
    >  ウィザードの既定の設定を使用する場合は、この手順を省略します。

1. をクリックして**完了**をで新しいプロジェクトを開き、ウィザードを閉じて**ソリューション エクスプ ローラー**します。

作成されたファイルを表示するには、プロジェクトが作成されると、**ソリューション エクスプ ローラー**します。 ウィザードでプロジェクト用に作成されるファイルの詳細については、プロジェクトが生成する ReadMe.txt ファイルを参照してください。 ファイルの種類についての詳細については、次を参照してください。 [Visual c プロジェクトに対して作成されるファイルの種類](../../ide/file-types-created-for-visual-cpp-projects.md)します。

## <a name="see-also"></a>関連項目

[Visual C++ プロジェクトの種類](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[プロパティ ページ](../../ide/property-pages-visual-cpp.md)
