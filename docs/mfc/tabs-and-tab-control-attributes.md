---
title: タブおよびタブ コントロールの属性
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: ca9f89565770e60a59007d609d132fae15eacae6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306458"
---
# <a name="tabs-and-tab-control-attributes"></a>タブおよびタブ コントロールの属性

タブ コントロールを構成するタブの動作と外観を細かく制御がある ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。 各タブには、ラベル、アイコン、項目の状態、および関連付けられている、アプリケーションで定義された 32 ビット値を持つことができます。 各タブでは、アイコン、ラベル、またはその両方を表示できます。

さらに、各タブ項目の 3 つの状態があります: 押された状態、元の状態、または強調表示されます。 この状態は、既存のタブ項目を変更することによってのみ設定できます。 呼び出しを使用して取得する既存のタブ項目を変更するには、 [GetItem](../mfc/reference/ctabctrl-class.md#getitem)、変更、`TCITEM`構造 (具体的には、 *dwState*と*dwStateMask*データ メンバー)、変更を返します`TCITEM`構造体への呼び出しで[SetItem](../mfc/reference/ctabctrl-class.md#setitem)します。 内のすべてのタブ項目の項目の状態をクリアする必要があるかどうか、`CTabCtrl`オブジェクト、呼び出しを行う[DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)します。 この関数は、すべてのタブの項目または現在選択されている 1 つを除くすべての項目の状態をリセットします。

次のコードでは、すべてのタブ アイテムの状態を解除し、3 番目の項目の状態を変更します。

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

タブの属性の詳細については、次を参照してください。[タブおよびタブ属性](/windows/desktop/Controls/tab-controls)Windows SDK に含まれています。 タブ コントロールにタブを追加する方法の詳細については、次を参照してください。[タブ コントロールを追加するタブ](../mfc/adding-tabs-to-a-tab-control.md)このトピックで後述します。

## <a name="see-also"></a>関連項目

[CTabCtrl の使い方](../mfc/using-ctabctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
