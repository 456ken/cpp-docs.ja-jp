---
title: ON_UPDATE_COMMAND_UI マクロ
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 986bc4f12223048a20f88da5d164b24dc1c08ace
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385353"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI マクロ

使用して、**プロパティ**ウィンドウにユーザー インターフェイス オブジェクトをコマンド ターゲット オブジェクトにコマンド更新ハンドラーに接続します。 ON_UPDATE_COMMAND_UI マクロにユーザー インターフェイス オブジェクトの ID を接続、ハンドラーを作成、更新プログラムを処理するオブジェクトに自動的にされます。 参照してください[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md)詳細についてはします。

たとえば、プログラムの編集] メニューで [すべてクリア コマンドを更新するには、次のように使用します、**プロパティ**コマンド更新ハンドラーの関数宣言を、選択したクラスのメッセージ マップ エントリを追加するウィンドウと呼ばれる`OnUpdateEditClearAll`クラス。宣言、およびクラスの実装ファイルには空の関数テンプレートです。 関数プロトタイプのようになります。

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

すべてのハンドラーは、関数に示すように、 **afx_msg**キーワード。 1 つの引数へのポインターにかかるすべての更新ハンドラーと同様に、`CCmdUI`オブジェクト。

## <a name="see-also"></a>関連項目

[方法: ユーザー インターフェイス オブジェクトを更新する](../mfc/how-to-update-user-interface-objects.md)
