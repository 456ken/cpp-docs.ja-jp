---
title: プロパティ シートとプロパティ ページ (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 7ff2851cc4ed04a64f1a49d68b6e3143b5edccd8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278764"
---
# <a name="property-sheets-and-property-pages-mfc"></a>プロパティ シートとプロパティ ページ (MFC)

MFC [ ダイアログ ボックス](../mfc/dialog-boxes.md)プロパティ シートとプロパティ ページに組み込むことにより実行できます。"タブ ダイアログ"を参照してください。 前後、または重ねて表示されたウィンドウのグループから見たファイル フォルダーのスタックと同様に、タブ付きのシートのスタックを格納する「プロパティ シート」と呼ばれる、MFC では、この種の Microsoft Word、Excel、および Visual C は、多くのダイアログ ボックスのようなダイアログ ボックスが表示されます。 フロント タブのコントロールが表示されます。ラベルの付いたタブだけでは、背面のタブに表示されます。 プロパティ シートは、多数のプロパティまたは複数のグループに分類できる設定を管理するために特に便利です。 通常、1 つのプロパティ シートは、いくつかの別のダイアログ ボックスを置き換えることで、ユーザー インターフェイスを簡略化できます。

プロパティ シートとプロパティ ページには、MFC バージョン 4.0 の時点でに Windows 95 および Windows NT version 3.51 以降に付属している一般的なコントロールを使用して実装されます。

プロパティ シートはクラスで実装[CPropertySheet](../mfc/reference/cpropertysheet-class.md)と[CPropertyPage](../mfc/reference/cpropertypage-class.md) (で説明されている、 *MFC リファレンス*)。 `CPropertySheet` に基づいて"複数"ページを含めることができますの全体的なダイアログ ボックスを定義します。`CPropertyPage`します。

プロパティ シートの作成と操作については、トピックを参照してください。[プロパティ シート](../mfc/property-sheets-mfc.md)します。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[ダイアログ ボックスの有効期間](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC のプロパティ シートとプロパティ ページ](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[データの交換](../mfc/exchanging-data.md)<br/>
[モードレス プロパティ シートの作成](../mfc/creating-a-modeless-property-sheet.md)<br/>
[[適用] ボタンの処理](../mfc/handling-the-apply-button.md)
