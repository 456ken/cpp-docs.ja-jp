---
title: リスト コントロールでの通知メッセージの処理
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 2a7899c74bfcddcdc8d54f7d9eb894553115ad66
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288073"
---
# <a name="processing-notification-messages-in-list-controls"></a>リスト コントロールでの通知メッセージの処理

ユーザーは、列ヘッダーをクリック、アイコンをドラッグして、ラベルというように、リスト コントロールの編集 ([CListCtrl](../mfc/reference/clistctrl-class.md))、親ウィンドウに通知メッセージを送信します。 応答として何らかの操作を行う場合は、これらのメッセージを処理します。 たとえば、ユーザーは、列ヘッダーをクリックすると、Microsoft Outlook のように、クリックされた列の内容に基づいて項目の並べ替えにする可能性があります。

ビューまたはダイアログ クラスのリスト コントロールから WM_NOTIFY メッセージの処理。 [プロパティ] ウィンドウを使用して作成する、 [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)ハンドラー関数を switch ステートメントが通知メッセージの処理に基づきます。

リスト コントロールが親ウィンドウに送信できる通知の一覧は、次を参照してください。[リスト ビュー コントロールのリファレンス](/windows/desktop/Controls/list-view-control-reference)Windows SDK に含まれています。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
