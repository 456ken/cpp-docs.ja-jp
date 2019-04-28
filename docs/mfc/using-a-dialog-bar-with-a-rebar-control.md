---
title: Rebar コントロールでのダイアログ バーの使い方
ms.date: 11/04/2016
f1_keywords:
- WM_EX_TRANSPARENT
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: 33ca3d0a7bf2e60511ea0048ad91b1f0930a2894
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180519"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Rebar コントロールでのダイアログ バーの使い方

説明したよう[Rebar コントロールとバンド](../mfc/rebar-controls-and-bands.md)、各バンドは、1 つだけの子ウィンドウ (またはコントロール) に含めることができます。 バンドごとに 1 つ以上の子ウィンドウを用意する場合、制限があります。 便利な回避策では、ダイアログ バー リソースの複数のコントロールを作成し、rebar コントロールに rebar バンド (ダイアログ バーを含む) を追加します。

通常、ダイアログ バー バンドを透明に表示する場合は、WS_EX_TRANSPARENT の拡張ダイアログ バーのオブジェクトのスタイルを設定します。 ただし、WS_EX_TRANSPARENT は正しくダイアログ バーの背景が描画いくつかの問題があるため、目的の効果を実現するために少しの余分な作業を行う必要があります。

次の手順の詳細、WS_EX_TRANSPARENT を使用せず、透過性を実現するために必要な手順は、スタイルを拡張します。

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Rebar バンドで透明なダイアログ バーを実装するには

1. 使用して、[クラスの追加 ダイアログ ボックス](../mfc/reference/adding-an-mfc-class.md)、新しいクラスを追加 (たとえば、 `CMyDlgBar`)、ダイアログ バー オブジェクトを実装します。

1. WM_ERASEBKGND メッセージのハンドラーを追加します。

1. 新しいハンドラーでは、次の例では、一致するように、既存のコードを変更します。

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. WM_MOVE メッセージ用のハンドラーを追加します。

1. 新しいハンドラーでは、次の例では、一致するように、既存のコードを変更します。

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

新しいハンドラーは、転送 WM_ERASEBKGND メッセージを親ウィンドウとダイアログ バーのオブジェクトを移動するたびに再描画を強制して、ダイアログ バーの透明度をシミュレートします。

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
