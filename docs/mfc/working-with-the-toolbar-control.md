---
title: ToolBar コントロールの操作
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 88c00bf60f2ce1fccecd757d13b2f814e3a18be4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260505"
---
# <a name="working-with-the-toolbar-control"></a>ToolBar コントロールの操作

この記事では、アクセスする方法について説明します、 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクトの基になる、 [CToolBar](../mfc/reference/ctoolbar-class.md)ツールバーをより細かく制御します。 これは、高度なトピックです。

## <a name="procedures"></a>手順

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>CToolBar オブジェクトを基になるツール バー コモン コントロールにアクセスするには

1. 呼び出す[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)します。

`GetToolBarCtrl` 参照を返します、 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクト。 ツールバーのコントロール クラスのメンバー関数を呼び出す、参照を使用できます。

> [!CAUTION]
>  呼び出し中に`CToolBarCtrl`**取得**関数が安全でを呼び出す場合、注意を使用して、**設定**関数。 これは、高度なトピックです。 通常、基になるツール バー コントロールにアクセスする必要はありません。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [コントロール (Windows のコモン コントロール)](../mfc/controls-mfc.md)

- [ツールバーに関する基本事項](../mfc/toolbar-fundamentals.md)

- [ドッキングとフローティング ツールバー](../mfc/docking-and-floating-toolbars.md)

- [ツールバーを動的にサイズ変更](../mfc/docking-and-floating-toolbars.md)

- [ツールバーのツール ヒント](../mfc/toolbar-tool-tips.md)

- [ステータス バーのフライ バイ更新](../mfc/toolbar-tool-tips.md)

- [ツール ヒントの通知の処理](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)と[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)クラス

- [カスタマイズ通知の処理](../mfc/handling-customization-notifications.md)

- [複数のツールバー](../mfc/toolbar-fundamentals.md)

- [古い形式のツールバーを使用します。](../mfc/using-your-old-toolbars.md)

- [コントロール バー](../mfc/control-bars.md)

Windows コモン コントロールの使い方の詳細については、次を参照してください。[コモン コントロール](/windows/desktop/Controls/common-controls-intro)します。

## <a name="see-also"></a>関連項目

[MFC ツール バーの実装](../mfc/mfc-toolbar-implementation.md)
