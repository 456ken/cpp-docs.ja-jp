---
title: オートメーション サーバー:オブジェクトの有効期間に関する問題
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: f9dbc6e4f321ba10fdffa013c158d53b84331e30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392895"
---
# <a name="automation-servers-object-lifetime-issues"></a>オートメーション サーバー:オブジェクトの有効期間に関する問題

オートメーション クライアントを作成または OLE 項目をアクティブ化、サーバー、クライアントにポインターを渡しますそのオブジェクト。 クライアントが OLE 関数の呼び出しを使用してオブジェクトへの参照を確立[iunknown::addref](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)します。 この参照は、クライアントが有効になって[:release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)します。 (Microsoft Foundation Class ライブラリの OLE クラスで記述されたクライアント アプリケーションでは、これらの呼び出しをする必要がなくなります。 フレームワークは)。OLE システムとサーバー自体には、オブジェクトへの参照を設定できます。 オブジェクトへの外部参照が有効に残っている限り、サーバーはオブジェクトを破棄できません。

フレームワークから派生した任意のサーバー オブジェクトへの参照の数の内部の回数を保持する[CCmdTarget](../mfc/reference/ccmdtarget-class.md)します。 この数は、ときに、オートメーション クライアントが更新またはその他のエンティティを追加またはオブジェクトへの参照を解放します。

参照カウントには、0 になると、フレームワークは仮想関数[CCmdTarget::OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease)します。 この関数の既定の実装、**削除**演算子をこのオブジェクトを削除します。

Microsoft Foundation Class ライブラリでは、外部クライアントがアプリケーションのオブジェクトへの参照がある場合は、アプリケーションの動作を制御するための追加機能を提供します。 各オブジェクトへの参照の数を保持するだけでなくは、サーバーは、アクティブなオブジェクトのグローバルなカウントを保持します。 グローバル関数[AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp)と[AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp)アクティブなオブジェクトのアプリケーションの数を更新します。 このカウントが 0 以外の場合は、アプリケーションをユーザーが システム メニューまたは ファイル メニューからの終了から閉じる終了しません。 代わりに、アプリケーションのメイン ウィンドウが非表示になります (ただし破棄されません) すべての保留中のクライアント要求が完了されるまでです。 通常、`AfxOleLockApp`と`AfxOleUnlockApp`オートメーションをサポートするクラスのそれぞれに、コンス トラクターとデストラクターで呼び出されます。

場合があります状況は、サーバー、クライアントがまだオブジェクトへの参照の終了が終了するを強制します。 など、サーバーが依存するリソースは使用できない場合、サーバー エラーが発生する原因となる可能性があります。 ユーザーは、他のアプリケーションが参照オブジェクトを含むサーバーのドキュメントを閉じるも可能性があります。

Windows SDK を参照してください。`IUnknown::AddRef`と`IUnknown::Release`します。

## <a name="see-also"></a>関連項目

[オートメーション サーバー](../mfc/automation-servers.md)<br/>
[AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)
