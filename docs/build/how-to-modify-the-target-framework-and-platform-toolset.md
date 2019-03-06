---
title: '方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更します。'
ms.custom: conceptual
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.modifytargetframeworkandplatformtoolset
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: 12f4f67eee59137042ef36f6709e921287d5528e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424775"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更します。

異なるバージョンの .NET Framework を対象として、別のプラットフォーム ツールセットを使用する Visual C プロジェクトの設定を変更することができます。 既定では、プロジェクト システムは、プロジェクトの作成に使用する Visual Studio のバージョンに対応する .NET Framework のバージョンおよびツールセットのバージョンを使用します。 プロジェクトのプロパティを変更することで、対象のプラットフォーム ツールセットを変更できます。 プロジェクト (.vcxproj) ファイルを変更すると、ターゲット フレームワークを変更できます。 それぞれの対象をコンパイルするために個別のコード ベースを保守する必要はありません。

> [!IMPORTANT]
>  エディションによっては、変更されたターゲット フレームワークまたはプラットフォーム ツールセットがサポートされていない場合があります。 互換性については、次を参照してください。[ポート、移行、および Visual Studio プロジェクトのアップグレード](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)します。

ターゲット フレームワークを変更すると、プラットフォーム ツールセットのバージョンもそのターゲット フレームワークをサポートするように変更されます。 たとえば、.NET Framework 4.5 を対象とする場合、Visual Studio 2015 (v140)、Visual Studio 2013 (v120)、Visual Studio 2012 (v110) のような互換性のあるプラットフォーム ツールセットを使用する必要があります。 .NET Framework 2.0、3.0、3.5、4、および x86、Itanium、x64 プラットフォームを対象とするには、 **Windows7.1SDK** プラットフォーム ツールセットを使用します。

> [!NOTE]
>  対象とするプラットフォーム ツールセットを変更するには、関連付けられたバージョンの Visual Studio または Windows プラットフォーム SDK がインストールされている必要があります。 たとえば、 **Windows7.1SDK** のプラットフォーム ツールセットを使って Itanium プラットフォームを対象とするには、 [Microsoft Windows SDK for Windows 7 と .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279) がインストールされている必要があります。ただし、正しい Framework のバージョンとプラットフォーム ツールセットを対象としている場合には、開発作業を行うために Visual Studio の別の互換性のあるバージョンを使います。

カスタム プラットフォーム ツールセットを作成することで、さらにターゲット フレームワークを拡張できます。 詳細については、Visual C++ チーム ブログの [C++ Native Multi-Targeting (C++ ネイティブ マルチ ターゲット)](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) をご覧ください。

### <a name="to-change-the-target-framework"></a>ターゲット フレームワークを変更するには

1. Visual Studio の **ソリューション エクスプローラー**で、プロジェクトを選びます。 メニュー バーで **[プロジェクト]** メニューを開き、 **[プロジェクトのアンロード]** を選択します。 これによって、プロジェクトのプロジェクト (.vcxproj) ファイルをアンロードします。

    > [!NOTE]
    >  Visual Studio ではプロジェクト ファイルの変更中には、C ++ プロジェクトを読み込むことはできません。 ただし、プロジェクトが Visual Studio に読み込まれるとき、メモ帳などの別のエディターを使用して、プロジェクト ファイルを変更することができます。 Visual Studio はプロジェクト ファイルが変更されたことを検知して、プロジェクトを再度読み込むように求めるメッセージが表示されます。

1. メニュー バーで、 **[ファイル]**、 **[開く]**、 **[ファイル]** の順に選択します。 **[ファイルを開く]** のダイアログ ボックスで、プロジェクトのフォルダーに移動し、プロジェクト (.vcxproj) ファイルを開きます。

1. プロジェクト ファイルで、ターゲット フレームワークのバージョンに対するエントリを見つけます。 たとえば、.NET Framework 4.5 を使用するプロジェクトの場合は、 `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` 要素の `<PropertyGroup Label="Globals">` 要素の中の `<Project>` を探します。 `<TargetFrameworkVersion>` 要素が存在しない場合には、プロジェクトは .NET Framework を使用しないため、変更の必要はありません。

1. その値を、使用するフレームワークのバージョン (v3.5 または v4.6 など) に更新します。

1. 変更を保存してエディターを閉じます。

1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロジェクトの再読み込み]** をクリックします。

1. 変更内容を確認するには、 **ソリューション エクスプローラー**で、右クリックして (ソリューションではなく) プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択してプロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 ダイアログ ボックスの左ペインで、 **[構成プロパティ]** を展開し、 **[全般]** を選択します。 **.NET Target 対象バージョン** が新しいバージョンのフレームワークを示していることを確認します。

### <a name="to-change-the-project-toolset"></a>プロジェクト ツールセットを変更するには

1. Visual Studio の **ソリューション エクスプローラー**で、(ソリューションではなく) プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択してプロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。

1. **[プロパティ ページ]** ダイアログ ボックスで、 **[構成]** ドロップダウン リストを開き、 **[すべての構成]** を選択します。

1. ダイアログ ボックスの左ペインで、 **[構成プロパティ]** を展開し、 **[全般]** を選択します。

1. 右ペインで、 **[プラットフォーム ツールセット]** をクリックして、ドロップダウン リストから使用するツールセットを選択します。 たとえば、Visual Studio 2010 のツールセットをインストールした場合選択**Visual Studio 2010 (v100)** プロジェクトに使用します。

1. **[OK]** を選択します。

## <a name="see-also"></a>関連項目

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
