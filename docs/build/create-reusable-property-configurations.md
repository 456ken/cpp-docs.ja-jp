---
title: Visual Studio プロジェクトの設定を共有または再利用する-C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: 9a8f6da3dc754aa9d47d46e26207a02bd1685ea8
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313190"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Visual Studio プロジェクトの設定を共有または再利用する

他のユーザーと共有したり、複数のプロジェクトで再利用したりできる設定のカスタムグループを作成するには、**プロパティマネージャー**を使用して*プロパティシート*(props ファイル) を作成し、再利用または共有できるようにする各種類のプロジェクトの設定を格納します。他にもあります。 プロパティシートを使用すると、"グローバル" 設定を作成する他の方法よりも、エラーが発生しやすくなります。 

> [!IMPORTANT]
> **.user ファイルとそれが問題になる理由**
>
> Visual Studio の過去のバージョンでは、.user ファイル名拡張子を持ち、\<userprofile>\AppData\Local\Microsoft\MSBuild\v4.0\ フォルダーにある、グローバル プロパティ シートを使っていました。 これらのファイルは、ユーザー単位、コンピューター単位でプロジェクト構成のプロパティを設定するため、現在はお勧めしていません。 このような "global" 設定は、特にビルド コンピューター上で複数のプラットフォームを対象とする場合にビルドに影響する可能性があります。 たとえば、MFC プロジェクトと Windows Phone プロジェクトの両方を持つ場合は、.user プロパティはいずれか 1 つに対して無効となります。 再利用可能なプロパティ シートは、より柔軟で堅牢です。
>
> 現在も .user ファイルは Visual Studio によってインストールされ、プロパティ継承に参加しますが、既定では空です。 最も良い方法は、プロジェクトがすべてのユーザー単位、コンピューター単位の設定に関係なく動作するように、**プロパティ マネージャー** でそれらへの参照を削除することです。これは、SCC (ソース コード管理) 環境で適切な動作が行われるようにするために重要です。

**プロパティマネージャー**を表示するには、メニューバーで、設定に応じて [**プロパティマネージャー**の**表示** > ] または [**その他のウィンドウ** > **プロパティマネージャー**の**表示** > ] をクリックします。

複数のプロジェクトに適用する、よく使用される共通のプロパティ セットがある場合は、**プロパティ マネージャー**を使ってそれらを再利用可能な "*プロパティ シート*" ファイルにキャプチャできます。これは慣例により .props ファイル名拡張子を持ちます。 プロパティを最初から設定しなくても済むように、そのシートを新しいプロジェクトに適用できます。

![プロパティ マネージャー ショートカット メニュー](media/sharingnew.png "SharingNew")

各構成ノードの下には、その構成に適用される各プロパティ シートのノードが表示されます。 ユーザーがプロジェクトを作成すると、システムはアプリ ウィザードでユーザーが選んだオプションに基づいて値を設定するプロパティ シートを追加します。 任意のノードを右クリックして [プロパティ] を選ぶと、そのノードに適用されるプロパティが表示されます。 すべてのプロパティ シートは、プロジェクトの "マスター" プロパティ シート (ms.cpp.props) に自動的にインポートされ、プロパティ マネージャーに表示される順序で評価されます。 プロパティ マネージャーで移動することにより、評価順序を変更することができます。 後で評価されるプロパティ シートにより、前に評価されたシートの値はオーバーライドされます。 .Vcxproj ファイル、props ファイル、.targets ファイル、環境変数、およびコマンドラインでの評価の順序の詳細については、「[プロジェクトのプロパティの継承](project-property-inheritance.md)」を参照してください。

**[新しいプロジェクト プロパティ シートの追加]** を選択してから、たとえば MyProps.props プロパティ シートを選ぶと、プロパティ ページ ダイアログ ボックスが表示されます。 これは MyProps プロパティ シートに適用されることに注意してください。行った変更は、プロジェクト ファイル (.vcxproj) ではなくシートに書き込まれます。

.vcxproj ファイルで同じプロパティが直接設定されている場合、プロパティ シートのプロパティはオーバーライドされます。

必要に応じて何度でもプロパティ シートをインポートできます。 ソリューション内の複数のプロジェクトが同じプロパティ シートから設定を継承することができ、プロジェクトは複数のシートを持つことができます。 プロパティ シート自体は別のプロパティ シートから設定を継承できます。

また、複数の構成に対して 1 つのプロパティ シートを作成できます。 これを行うには、各構成のプロパティ シートを作成し、そのうちの 1 つのショートカット メニューを開き、 **[既存のプロパティ シートの追加]** を選んで、他のシートを追加します。 ただし、1 つの共通のプロパティ シートを使用する場合は、プロパティを設定するときにシートが適用されるすべての構成セットが取得されることや、IDE では指定されたプロパティ シートから継承されるプロジェクトまたは他のプロパティ シートが表示されないことに注意してください。

多くのプロジェクトを持つ大規模なソリューションでは、ソリューション レベルでプロパティ シートを作成すると便利な場合があります。 ソリューションにプロジェクトを追加する場合、プロジェクトにそのプロパティ シートを追加するには、**プロパティ マネージャー**を使います。 プロジェクト レベルでの必要に応じて、新規プロパティ シートを追加してプロジェクト固有の値を設定できます。

> [!IMPORTANT]
> 既定では、.props ファイルはプロジェクト項目として作成されていないため、ソース管理に含まれません。 ソース管理に含める場合は、ソリューション項目として手動でファイルを追加できます。

#### <a name="to-create-a-property-sheet"></a>プロパティ シートを作成するには

1. メニューバーで、[**表示** > **プロパティマネージャー**または**その他のウィンドウ** > **プロパティマネージャー**を**表示** > します] を選択します。 **プロパティ マネージャー**が開きます。

2. プロパティ シートのスコープを定義するには、適用する項目を選択します。 これは、特定の構成または別のプロパティ シートです。 この項目のショートカット メニューを開き、 **[新しいプロジェクト プロパティ シートの追加]** を選びます。 名前と場所を指定します。

3. **プロパティ マネージャー**で新しいプロパティ シートを開き、含めるプロパティを設定します。
