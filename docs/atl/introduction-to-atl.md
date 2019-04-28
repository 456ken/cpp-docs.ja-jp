---
title: ATL の概要
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
ms.openlocfilehash: 8c2dcab962cd9863acf0f8e7070727f3b18117d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261918"
---
# <a name="introduction-to-atl"></a>ATL の概要

ATL Active Template Library は、一連のテンプレート ベースの C++ クラスに簡単に作成できると、小規模で高速コンポーネント オブジェクト モデル (COM) オブジェクト。 キーの COM 機能を含む特別なサポートしています: の実装のストック[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)、 [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)、 [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)と`IDispatch`デュアル;インターフェイスです。標準の COM 列挙子インターフェイス。コネクション ポイント。ティアオフ インターフェイスです。ActiveX コントロールとします。

ATL コードは、シングル スレッド オブジェクト、アパートメント モデルのオブジェクト、フリー スレッド モデル オブジェクト、またはフリー スレッドとアパートメント モデルの両方のオブジェクトを作成するために使用できます。

このセクションで説明したトピックは次のとおりです。

- どの、[テンプレート ライブラリ](../atl/using-a-template-library.md)標準ライブラリとは異なります。

- どのようなこと[でき、ATL は実行できない](../atl/scope-of-atl.md)します。

- [ATL と MFC の選択に関する推奨事項](../atl/recommendations-for-choosing-between-atl-and-mfc.md)します。

## <a name="see-also"></a>関連項目

[COM と ATL の概要](../atl/introduction-to-com-and-atl.md)
