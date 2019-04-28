---
title: CHandle クラス
ms.date: 11/04/2016
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 19e761ea8eb133db55b4d24600f2a1fd01ac3e34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245635"
---
# <a name="chandle-class"></a>CHandle クラス

このクラスは、作成してオブジェクトのハンドルを使用するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class CHandle
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|コンストラクターです。|
|[CHandle:: ~ CHandle](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHandle::Attach](#attach)|アタッチするには、このメソッドを呼び出す、`CHandle`オブジェクトを既存のハンドルにします。|
|[CHandle::Close](#close)|閉じるには、このメソッドを呼び出して、`CHandle`オブジェクト。|
|[CHandle::Detach](#detach)|ハンドルをデタッチするには、このメソッドを呼び出す、`CHandle`オブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CHandle::operator ハンドル](#operator_handle)|格納されたハンドルの値を返します。|
|[CHandle::operator =](#operator_eq)|代入演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CHandle::m_h](#m_h)|ハンドルを格納するメンバー変数です。|

## <a name="remarks"></a>Remarks

A`CHandle`ハンドルが必要な場合に、オブジェクトを使用できます。 主な違いは、`CHandle`オブジェクトは自動的に削除されます。

> [!NOTE]
>  一部の API 関数は、INVALID_HANDLE_VALUE を使用しながら、空または無効なハンドルでは、として NULL を使用します。 `CHandle` だけが使用され、NULL では、実際のハンドルとして INVALID_HANDLE_VALUE を処理します。 INVALID_HANDLE_VALUE を返す可能性のある API を呼び出す場合は、呼び出す前にこの値をチェックする必要があります[CHandle::Attach](#attach)に渡すか、`CHandle`コンス トラクターを代わりに NULL を渡します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="attach"></a>  CHandle::Attach

アタッチするには、このメソッドを呼び出す、`CHandle`オブジェクトを既存のハンドルにします。

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>パラメーター

*h*<br/>
`CHandle` ハンドルの所有権を*h*します。

### <a name="remarks"></a>Remarks

割り当てます、`CHandle`オブジェクトを*h*を処理します。 デバッグ ビルドは atlassert 場合*h*は NULL です。 ハンドルの妥当性に関するその他のチェックは行われません。

##  <a name="chandle"></a>  CHandle::CHandle

コンストラクターです。

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>パラメーター

*h*<br/>
既存のハンドルまたは`CHandle`します。

### <a name="remarks"></a>Remarks

新たに作成`CHandle`必要に応じて既存のハンドルを使用して、オブジェクトまたは`CHandle`オブジェクト。

##  <a name="dtor"></a>  CHandle:: ~ CHandle

デストラクターです。

```
~CHandle() throw();
```

### <a name="remarks"></a>Remarks

解放、`CHandle`オブジェクトを呼び出すことによって[CHandle::Close](#close)します。

##  <a name="close"></a>  CHandle::Close

閉じるには、このメソッドを呼び出して、`CHandle`オブジェクト。

```
void Close() throw();
```

### <a name="remarks"></a>Remarks

オブジェクトの開いているハンドルを閉じます。 ハンドルがある場合、NULL のかどうか`Close`が既に呼び出されると、ATLASSERT がデバッグ ビルドで発生します。

##  <a name="detach"></a>  CHandle::Detach

ハンドルをデタッチするには、このメソッドを呼び出す、`CHandle`オブジェクト。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>戻り値

デタッチされているハンドルを返します。

### <a name="remarks"></a>Remarks

ハンドルの所有権を解放します。

##  <a name="m_h"></a>  CHandle::m_h

ハンドルを格納するメンバー変数です。

```
HANDLE m_h;
```

##  <a name="operator_eq"></a>  CHandle::operator =

代入演算子です。

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>パラメーター

*h*<br/>
`CHandle` ハンドルの所有権を*h*します。

### <a name="return-value"></a>戻り値

新しいへの参照を返します`CHandle`オブジェクト。

### <a name="remarks"></a>Remarks

場合、`CHandle`オブジェクトが現在のハンドルを含むは閉じられます。 `CHandle`オブジェクトを NULL に設定のハンドルの参照で渡される必要があります。 これにより、2 つ`CHandle`オブジェクトが同じアクティブなハンドルを含めることはありません。

##  <a name="operator_handle"></a>  CHandle::operator ハンドル

格納されたハンドルの値を返します。

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Remarks

格納されている値を返します[CHandle::m_h](#m_h)します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
