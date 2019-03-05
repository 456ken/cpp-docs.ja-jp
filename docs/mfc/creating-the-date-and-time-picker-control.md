---
title: 日時指定コントロールの作成
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: b3dd04d917667ff04001a455263d2a2f4af9bf9c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282072"
---
# <a name="creating-the-date-and-time-picker-control"></a>日時指定コントロールの作成

日付と時刻の選択コントロールを作成する方法は、ダイアログ ボックスで、コントロールの使用または以外のウィンドウで作成するかどうかによって異なります。

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>ダイアログ ボックスで直接 CDateTimeCtrl を使用するには

1. ダイアログ エディターでダイアログ テンプレート リソースを日付と時刻の選択コントロールを追加します。 そのコントロールの ID を指定します

1. 日付と時刻の選択コントロールのプロパティ ダイアログ ボックスを使用して、必要なスタイルを指定します。

1. 使用して、[メンバー変数の追加ウィザード](../ide/adding-a-member-variable-visual-cpp.md)型のメンバー変数を追加する[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)コントロール プロパティにします。 このメンバーを使用するには、呼び出しと`CDateTimeCtrl`メンバー関数。

1. [プロパティ] ウィンドウを使用して、日時指定コントロールのダイアログ クラスのハンドラー関数にマップする[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)メッセージを処理する必要があります (を参照してください[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md))。

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)、追加のスタイルを設定、`CDateTimeCtrl`オブジェクト。

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>CDateTimeCtrl を以外のウィンドウで使用するには

1. ビューまたはウィンドウのクラス内のコントロールを宣言します。

1. コントロールの呼び出し[作成](../mfc/reference/ctabctrl-class.md#create)メンバー関数は、おそらくで[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)、親ウィンドウの可能性がありますの早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate)いる場合、ハンドラー関数コントロールをサブクラス)。 コントロールのスタイルを設定します。

## <a name="see-also"></a>関連項目

[CDateTimeCtrl の使い方](../mfc/using-cdatetimectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
