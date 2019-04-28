---
title: CComPtr クラス
ms.date: 11/04/2016
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 5e3e510291daa50ddcf5d63451edef0428d66ed1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259106"
---
# <a name="ccomptr-class"></a>CComPtr クラス

COM インターフェイス ポインターを管理するためのスマート ポインター クラスです。

## <a name="syntax"></a>構文

```
template<class T>
class CComPtr
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
COM インターフェイスを格納するポインターの種類を指定します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|コンストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|メンバーのポインターにポインターを割り当てます。|

## <a name="remarks"></a>Remarks

ATL を使用して`CComPtr`と[CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM インターフェイス ポインターを管理します。 派生両方[CComPtrBase](../../atl/reference/ccomptrbase-class.md)、両方は、自動参照カウントを実行するとします。

`CComPtr`と[CComQIPtr](../../atl/reference/ccomqiptr-class.md)クラスは、自動参照カウントを実行することによってメモリ リークを解決できます。  次の関数は両方が、同じ論理操作を実行します。ただし、どのように 2 番目のバージョンがありますエラーの発生を使用して、`CComPtr`クラス。

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

デバッグ ビルドでは、コードのトレースの atlsd.lib をリンクします。

## <a name="inheritance-hierarchy"></a>継承階層

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="ccomptr"></a>  CComPtr::CComPtr

コンストラクターです。

```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>パラメーター

*lp*<br/>
インターフェイス ポインターを初期化するために使用されます。

*T*<br/>
COM インターフェイスです。

##  <a name="operator_eq"></a>  CComPtr::operator =

代入演算子。

```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>戻り値

更新されたポインターを返します`CComPtr`オブジェクト

### <a name="remarks"></a>Remarks

この AddRefs 新しいオブジェクトを操作して解放場合は、1 つの既存のオブジェクトが存在します。

## <a name="see-also"></a>関連項目

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
