---
title: ATL プロパティ ページを追加します。
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: c61f666865d3e1db4cdcf2dc6d3e07c2113a79c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249100"
---
# <a name="adding-an-atl-property-page"></a>ATL プロパティ ページを追加します。

Active Template Library (ATL) のプロパティ ページをプロジェクトに追加するには、プロジェクトする必要がありますが作成されたら、ATL アプリケーションまたは ATL サポートを含む MFC アプリケーションとして。 使用することができます、 [ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)ATL アプリケーションの作成または[ATL オブジェクトを MFC アプリケーションに追加](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)MFC アプリケーションの ATL サポートを実装します。

コントロールのプロパティ ページを追加する場合、コントロールをサポートする必要があります、 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)インターフェイス。 このインターフェイスは、コントロールの派生リストで、既定では、クラスを[ATL のコントロールを作成](../../atl/reference/adding-an-atl-control.md)を使用して、 [ATL コントロール ウィザード](../../atl/reference/atl-control-wizard.md)します。

> [!NOTE]
> コントロール クラスを持たない場合[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)の派生リストにする必要があります手動で追加します。

## <a name="to-add-an-atl-property-page-to-your-project"></a>ATL プロパティ ページをプロジェクトに追加するには

1. いずれかで**ソリューション エクスプ ローラー**または[クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)、ATL プロパティ ページを追加するプロジェクトの名前を右クリックします。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**クラスの追加**します。

1. [クラスの追加](../../ide/add-class-dialog-box.md) ダイアログ ボックスで、**テンプレート**ウィンドウで、をクリックして**ATL プロパティ ページ**順にクリックします**オープン**を表示する[ATL プロパティ ページ ウィザード](../../atl/reference/atl-property-page-wizard.md)します。

指定する必要がありますコントロールのプロパティ ページを作成すると、 [PROP_PAGE](property-map-macros.md#prop_page)コントロールのプロパティ マップ内のエントリ。

## <a name="see-also"></a>関連項目

[プロパティ ページ](../../atl/atl-com-property-pages.md)<br/>
[ATL COM オブジェクトの基礎](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[例:プロパティ ページの実装](../../atl/example-implementing-a-property-page.md)
