---
title: 通常オーバーライドされるメンバー関数
ms.date: 11/04/2016
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 26a1527dbdac4b2a9deb57fb13481f8d2f9cb5b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263820"
---
# <a name="commonly-overridden-member-functions"></a>通常オーバーライドされるメンバー関数

最も一般的にオーバーライドするメンバー関数を一覧表示、次の表、 `CDialog`-クラスを派生します。

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>通常オーバーライドされる CDialog のクラスのメンバー関数

|メンバー関数|メッセージに応答するには|オーバーライドの目的|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|ダイアログ ボックスのコントロールを初期化します。|
|`OnOK`|**BN_CLICKED**ボタンの**IDOK**|ユーザーが [ok] ボタンをクリックしたときに応答します。|
|`OnCancel`|**BN_CLICKED**ボタンの**IDCANCEL**|ユーザーが [キャンセル] ボタンをクリックしたときに応答します。|

`OnInitDialog`、 `OnOK`、および`OnCancel`は仮想関数。 これらをオーバーライドする派生ダイアログ クラスを使用してオーバーライドする関数を宣言する、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。

`OnInitDialog` ダイアログ ボックスが表示される直前に呼び出されます。 既定値を呼び出す必要があります`OnInitDialog`ハンドラー、オーバーライドから、通常は、ハンドラーの最初のアクションとして。 既定では、`OnInitDialog`返します**TRUE**  ダイアログ ボックスで、最初のコントロールにフォーカスを設定する必要があることを示します。

`OnOK` 通常、モードレスがないモーダル ダイアログ ボックスのオーバーライドされます。 モーダル ダイアログ ボックスのこのハンドラーをオーバーライドする場合は、オーバーライドから基底クラスのバージョンを呼び出す — ことを確認する`EndDialog`が呼び出されます: 呼び出したり`EndDialog`自分でします。

`OnCancel` モードレス ダイアログ ボックスに、通常はオーバーライドされます。

これらのメンバー関数の詳細については、クラスを参照してください。 [CDialog](../mfc/reference/cdialog-class.md)で、 *MFC リファレンス*についての説明と[ ダイアログ ボックスのライフ サイクル](../mfc/life-cycle-of-a-dialog-box.md)します。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[通常追加されるメンバー関数](../mfc/commonly-added-member-functions.md)
