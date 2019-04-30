---
title: CD2DRectF クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 8e5c22fe15ce0d930f81dd16673927d5299bf630
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396276"
---
# <a name="cd2drectf-class"></a>CD2DRectF クラス

`D2D1_RECT_F`のラッパー。

## <a name="syntax"></a>構文

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|オーバーロードされます。 構築、`CD2DRectF`オブジェクトから`D2D1_RECT_F`オブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|返します、**ブール**式に有効なデータ (NULL) がないかどうかを示す値です。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DRectF::operator CRect](#operator_crect)|変換`CD2DRectF`に`CRect`オブジェクト。|

## <a name="inheritance-hierarchy"></a>継承階層

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

CRect オブジェクトから CD2DRectF オブジェクトを構築します。

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
  CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
元の四角形

*fLeft*<br/>
ソースの左座標

*fTop*<br/>
ソースの上座標

*fRight*<br/>
右側の座標のソース

*fBottom*<br/>
ソースの下端の座標

##  <a name="isnull"></a>  CD2DRectF::IsNull

式に有効なデータ (Null) がないかどうかを示すブール値を返します。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>戻り値

四角形の上、左、下、および適切な値が 0 に等しい場合は TRUE。それ以外の場合は FALSE です。

##  <a name="operator_crect"></a>  CD2DRectF::operator CRect

CD2DRectF CRect オブジェクトに変換します。

```
operator CRect();
```

### <a name="return-value"></a>戻り値

D2D の四角形の現在の値。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
