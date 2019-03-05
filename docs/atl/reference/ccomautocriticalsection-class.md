---
title: CComAutoCriticalSection クラス
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 613440eceb71f0277f4cc5de2af89fe263772797
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301611"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection クラス

`CComAutoCriticalSection` 取得とクリティカル セクション オブジェクトの所有権を解放するメソッドを提供します。

## <a name="syntax"></a>構文

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|コンストラクターです。|
|[CComAutoCriticalSection::~CComAutoCriticalSection](#dtor)|デストラクターです。|

## <a name="remarks"></a>Remarks

`CComAutoCriticalSection` クラスに似ていますが[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)、除く`CComAutoCriticalSection`コンス トラクターでクリティカル セクション オブジェクトを自動的に初期化します。

通常、使用して`CComAutoCriticalSection`を通じて、`typedef`名前[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)します。 この名前の参照`CComAutoCriticalSection`とき[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)が使用されています。

`Init`と`Term`メソッドから[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)このクラスを使用する場合は使用できません。

## <a name="inheritance-hierarchy"></a>継承階層

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

コンストラクターです。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Remarks

Win32 関数を呼び出す[InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection)、クリティカル セクション オブジェクトを初期化します。

##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection

デストラクターです。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Remarks

デストラクターの呼び出し[DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection)、クリティカル セクション オブジェクトによって使用されるすべてのシステム リソースを解放します。

## <a name="see-also"></a>関連項目

[CComFakeCriticalSection クラス](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection クラス](../../atl/reference/ccomcriticalsection-class.md)
