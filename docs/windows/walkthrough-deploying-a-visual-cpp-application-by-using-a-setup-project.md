---
title: 'チュートリアル: セットアップ プロジェクトを使用した Visual C++ アプリケーションの配置'
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 6829e917ed0a0e27bea7f42eb9bcfb2b9ad5d2e1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877377"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>チュートリアル: セットアップ プロジェクトを使用した Visual C++ アプリケーションの配置

セットアップ プロジェクトを使用して、Visual C++ アプリケーションを展開する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio がインストールされているコンピューター。

- Visual C++ ライブラリがない別のコンピューター。

## <a name="create-the-setup-project"></a>セットアップ プロジェクトを作成します。

セットアップ プロジェクトを作成する方法については、インストールした Visual Studio のバージョンによって異なります。 バージョン セレクターで、適切なバージョンに設定して左上にあることを確認します。

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Visual Studio 2019 でプロジェクトを作成するには

1. メニュー バーで、**ファイル** > **新規** > **プロジェクト**を開く、**新しいプロジェクトを作成** ダイアログ ボックス。

   ![MFC アプリケーション プロジェクト](media/vs2019-mfc-app-new-project.png "新しい MFC アプリケーション")

1. ダイアログの上部にある次のように入力します。 `MFC` 、検索ボックスをクリック**MFC アプリ**結果リストから。 Windows [スタート] メニューから Visual Studio インストーラー プログラムを起動し、をクリックする必要がありますいない場合、  **C++デスクトップ開発ワークロード**を並べて表示します。 **個々 のコンポーネント**、MFC コンポーネントが選択されていることを確認します。

1. 次のページで、プロジェクトの名前を入力し、必要な場合は、プロジェクトの場所を指定します。

1. 選択、**作成**クライアント プロジェクトを作成するボタンをクリックします。 ときに、 **MFC アプリケーション ウィザード**が表示されたら、すべての既定値をそのまま使用します。

1. アクティブなソリューション構成を **[解放]** に変更します。 **[ビルド]** メニューの **[構成マネージャー]** を選択します。 **[構成マネージャー]** ダイアログ ボックスで、**[アクティブ ソリューション構成]** ドロップダウン ボックスの **[解放]** をクリックします。 **[閉じる]** をクリックします。

1. **Ctrl**+**Shift**+**B**B キーを押して、アプリケーションをビルドします。 または、**[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。 アプリケーションをビルドすると、セットアップ プロジェクトでこの MFC アプリケーション プロジェクトの出力を使用できます。

1. Microsoft Visual Studio Installer Projects の拡張機能をまだダウンロードしていない場合は、これをダウンロードします。 この拡張機能は、Visual Studio 開発者向けの無料版であり、Visual Studio にセットアップおよび配置プロジェクト テンプレートの機能を追加するものです。 Visual Studio で、インターネットに接続しているときに選択**拡張** > **拡張機能の管理**します。 **[拡張機能と更新プログラム]** ダイアログ ボックスで **[オンライン]** タブを選択し、検索ボックスに「*Microsoft Visual Studio Installer Projects*」と入力します。 キーを押して**Enter**を選択します**Microsoft Visual Studio\<バージョン > インストーラー プロジェクト**、 をクリック**ダウンロード**します。 拡張機能を実行してインストールするよう選択し、Visual Studio を再起動します。

   ![Visual Studio セットアップ プロジェクト](media/vs2019-extension-dialog-installer-project.png "クライアント プロジェクトの名前")

1. Visual Studio メニュー バーで、**ファイル** > **最近使ったプロジェクトおよびソリューション**プロジェクトを再び開くように選択します。

1. メニュー バーで、**ファイル** > **新規** > **プロジェクト**を開く、**新しいプロジェクトを作成** ダイアログ ボックス。 検索ボックスで、「セットアップ」を入力し、結果の一覧から選択**セットアップ プロジェクト**します。

1. **[名前]** ボックスにセットアップ プロジェクトの名前を入力します。 **[ソリューション]** ドロップダウン リストで **[ソリューションに追加]** をクリックします。 **[OK]** をクリックすると、セットアップ プロジェクトが作成されます。 **[File Assistant (ProjectName)]/(ファイル アシスタント (<プロジェクト名>)/)** タブがエディター ウィンドウで開きます。

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Visual Studio 2017 でプロジェクトを作成するには

1. 新しいプロジェクトを作成します。 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

1. 使用して、 **MFC アプリケーション ウィザード**新しい Visual Studio ソリューションを作成します。 ウィザードを見つけるには、**[新しいプロジェクト]** ダイアログ ボックスで、**Visual C++** ノードを展開し、**[MFC]**、**[MFC アプリケーション]** の順に選択して、プロジェクトの名前を入力し、**[OK]** をクリックします。 **[完了]** をクリックします。

   > [!NOTE]
   > 場合、 **MFC アプリケーション**型がない場合、選択**Visual Studio インストーラーを開く**の左側のウィンドウで、**新しいプロジェクト** ダイアログ ボックス。 **[省略可能]** コンポーネント セクションの **[C++ によるデスクトップ開発]** で、"**x86 用と x64 用の Visual C++ MFC**" という名前のオプションをインストールします。

1. アクティブなソリューション構成を **[解放]** に変更します。 **[ビルド]** メニューの **[構成マネージャー]** を選択します。 **[構成マネージャー]** ダイアログ ボックスで、**[アクティブ ソリューション構成]** ドロップダウン ボックスの **[解放]** をクリックします。 **[閉じる]** をクリックします。

1. **Ctrl**+**Shift**+**B**B キーを押して、アプリケーションをビルドします。 または、**[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。 アプリケーションをビルドすると、セットアップ プロジェクトでこの MFC アプリケーション プロジェクトの出力を使用できます。

1. Microsoft Visual Studio Installer Projects の拡張機能をまだダウンロードしていない場合は、これをダウンロードします。 この拡張機能は、Visual Studio 開発者向けの無料版であり、Visual Studio にセットアップおよび配置プロジェクト テンプレートの機能を追加するものです。 インターネットに接続しているときに、Visual Studio で、**[ツール]** > **[拡張機能と更新プログラム]** を選択します。 **[拡張機能と更新プログラム]** ダイアログ ボックスで **[オンライン]** タブを選択し、検索ボックスに「*Microsoft Visual Studio Installer Projects*」と入力します。 キーを押して**Enter**を選択します**Microsoft Visual Studio\<バージョン > インストーラー プロジェクト**、 をクリック**ダウンロード**します。 拡張機能を実行してインストールするよう選択し、Visual Studio を再起動します。

1. メニュー バーで、**ファイル** > **最近使ったプロジェクトおよびソリューション**プロジェクトを再び開くように選択します。

1. メニュー バーで **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し、**[新しいプロジェクト]** ダイアログ ボックスを開きます。 次に、ダイアログ ボックスの左ウィンドウで、**[インストール済み]** > **[その他のプロジェクトの種類]** ノードを展開し、**[Visual Studio インストーラー]** を選択します。 中央のウィンドウで、**[Setup Project]\(セットアップ プロジェクト\)** を選択します。

1. **[名前]** ボックスにセットアップ プロジェクトの名前を入力します。 **[ソリューション]** ドロップダウン リストで **[ソリューションに追加]** をクリックします。 **[OK]** をクリックすると、セットアップ プロジェクトが作成されます。 **[File Assistant (ProjectName)]/(ファイル アシスタント (<プロジェクト名>)/)** タブがエディター ウィンドウで開きます。

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Visual Studio 2015 でプロジェクトを作成するには

1. 新しいプロジェクトを作成します。 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

1. 使用して、 **MFC アプリケーション ウィザード**新しい Visual Studio ソリューションを作成します。 ウィザードを見つけるには、**[新しいプロジェクト]** ダイアログ ボックスで、**Visual C++** ノードを展開し、**[MFC]**、**[MFC アプリケーション]** の順に選択して、プロジェクトの名前を入力し、**[OK]** をクリックします。 **[完了]** をクリックします。

   > [!NOTE]
   > 場合、 **MFC アプリケーション**型が見つかりません、種類と Windows のスタート ボタンをクリックします**プログラムの追加と削除**します。 結果の一覧からプログラムを開き、インストールされているプログラムの一覧で、Microsoft Visual Studio 2015 のインストールを見つけます。 これをダブルクリックし、**[変更]** を選択して、**[Visual C++]** で **[Microsoft Foundation Classes]** コンポーネントを選択します。

1. アクティブなソリューション構成を **[解放]** に変更します。 **ビルド**メニューの  **Configuration Manager**します。 **[構成マネージャー]** ダイアログ ボックスで、**[アクティブ ソリューション構成]** ドロップダウン ボックスの **[解放]** をクリックします。 **[閉じる]** をクリックします。

1. **Ctrl**+**Shift**+**B**B キーを押して、アプリケーションをビルドします。 または、**[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。 アプリケーションをビルドすると、セットアップ プロジェクトでこの MFC アプリケーション プロジェクトの出力を使用できます。

1. Microsoft Visual Studio Installer Projects の拡張機能をまだダウンロードしていない場合は、これをダウンロードします。 この拡張機能は、Visual Studio 開発者向けの無料版であり、Visual Studio にセットアップおよび配置プロジェクト テンプレートの機能を追加するものです。 インターネットに接続しているときに、Visual Studio で、**[ツール]** > **[拡張機能と更新プログラム]** を選択します。 **[拡張機能と更新プログラム]** ダイアログ ボックスで **[オンライン]** タブを選択し、検索ボックスに「*Microsoft Visual Studio Installer Projects*」と入力します。 キーを押して**Enter**を選択します**Microsoft Visual Studio\<バージョン > インストーラー プロジェクト**、 をクリック**ダウンロード**します。 拡張機能を実行してインストールするよう選択し、Visual Studio を再起動します。

1. メニュー バーで、**ファイル** > **最近使ったプロジェクトおよびソリューション**プロジェクトを再び開くように選択します。

1. メニュー バーで **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し、**[新しいプロジェクト]** ダイアログ ボックスを開きます。 次に、ダイアログ ボックスの左ウィンドウで、**[インストール済み]** > **[その他のプロジェクトの種類]** ノードを展開し、**[Visual Studio インストーラー]** を選択します。 中央のウィンドウで、**[Setup Project]\(セットアップ プロジェクト\)** を選択します。

1. **[名前]** ボックスにセットアップ プロジェクトの名前を入力します。 **[ソリューション]** ドロップダウン リストで **[ソリューションに追加]** をクリックします。 **[OK]** をクリックすると、セットアップ プロジェクトが作成されます。 **[File Assistant (ProjectName)]/(ファイル アシスタント (<プロジェクト名>)/)** タブがエディター ウィンドウで開きます。

::: moniker-end

## <a name="add-items-to-the-project"></a>項目をプロジェクトに追加します。

1. **[アプリケーション フォルダー]** ノードを右クリックし、**[追加]** > **[プロジェクト出力]** を選択して、**[プロジェクト出力グループの追加]** ダイアログ ボックスを開きます。 ダイアログ ボックスで **[プライマリ出力]** を選択し、**[OK]** をクリックします。 **[Primary Output from ProjectName (Active)]\(<プロジェクト名> (アクティブ) のプライマリ出力\)** という名前の新しい項目が表示されます。

1. **[アプリケーション フォルダー]** ノードを右クリックし、**[追加]** > **[アセンブリ]** を選択して、**[コンポーネントの選択]** ダイアログボックスを開きます。 「[再配布する DLL の決定](determining-which-dlls-to-redistribute.md)」の記事で説明されているように、プログラムで必要なすべての DLL を選択して追加します。

1. **[Primary Output from ProjectName (Active)]\(<プロジェクト名> (アクティブ) のプライマリ出力\)** 項目を選択し、**[Create Shortcut to Primary Output from ProjectName (Active)]\(<プロジェクト名> (アクティブ) のプライマリ出力へのショートカットを作成\)** を右クリックします。 **[Shortcut to Primary Output from ProjectName (Active)]\(<プロジェクト名> (アクティブ) のプライマリ出力へのショートカット\)** という名前の新しい項目が表示されます。 ショートカット項目の名前を変更し、ウィンドウの左側にある **[ユーザーのプログラム メニュー]** ノードに項目をドラッグ アンド ドロップすることもできます。

1. メニュー バーで **[ビルド]** > **[構成マネージャー]** の順に選択します。 **[プロジェクト]** テーブルの **[ビルド]** 列で、配置プロジェクトのボックスをオンにします。 **[閉じる]** をクリックします。

1. メニュー バーで **[ビルド]** > **[ソリューションのビルド]** の順に選択して、MFC プロジェクトと配置プロジェクトをビルドします。

1. ソリューション フォルダーで、配置プロジェクトからビルドされた setup.exe プログラムを見つけます。 このファイル (および .msi ファイル) をコピーして、アプリケーションとその必要なライブラリ ファイルを別のコンピューターにインストールできます。 Visual C ++ ライブラリがない 2 台目のコンピューターで、セットアップ プログラムを実行します。

## <a name="see-also"></a>関連項目

[配置例](deployment-examples.md)<br/>
