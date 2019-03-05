---
title: CLinearTransition クラス
ms.date: 11/04/2016
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
ms.openlocfilehash: 4aa2d9955d2bbf98d2d7829806c4bcbd76340847
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270801"
---
# <a name="clineartransition-class"></a>CLinearTransition クラス

線形遷移をカプセル化します。

## <a name="syntax"></a>構文

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CLinearTransition::CLinearTransition](#clineartransition)|線形遷移オブジェクトを構築し、期間と最終的な値で初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CLinearTransition::Create](#create)|カプセル化された移行 COM オブジェクトを作成する遷移ライブラリを呼び出します。 (上書き[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create))。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|移行の最後にアニメーション変数の値。|
|[CLinearTransition::m_duration](#m_duration)|移行の期間です。|

## <a name="remarks"></a>Remarks

、線形遷移中には、アニメーション変数の値はその初期値から指定した最終的な値に直線的に移行します。 すべての遷移が自動的にクリアされますが、お勧めするそれらに割り当てられている新しい演算子を使用します。 カプセル化された IUIAnimationTransition COM オブジェクトは、null を指定し、まで、CAnimationController::AnimateGroup によって作成されます。 影響を与えませんこの COM オブジェクトの作成後は、メンバー変数を変更します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransition](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="clineartransition"></a>  CLinearTransition::CLinearTransition

線形遷移オブジェクトを構築し、期間と最終的な値で初期化します。

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>パラメーター

*duration*<br/>
移行の期間です。

*dblFinalValue*<br/>
移行の最後にアニメーション変数の値。

##  <a name="create"></a>  CLinearTransition::Create

カプセル化された移行 COM オブジェクトを作成する遷移ライブラリを呼び出します。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>パラメーター

*pLibrary*<br/>
ポインター、 [IUIAnimationTransitionLibrary インターフェイス](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)、標準的な遷移のライブラリを定義します。

### <a name="return-value"></a>戻り値

移行が正常に作成された場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_dblfinalvalue"></a>  CLinearTransition::m_dblFinalValue

移行の最後にアニメーション変数の値。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_duration"></a>  CLinearTransition::m_duration

移行の期間です。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
