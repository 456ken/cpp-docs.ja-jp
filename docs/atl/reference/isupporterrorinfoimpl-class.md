---
title: ISupportErrorInfoImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: f7e300e30ff0f14b56d2a1bae86b00e090674679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274766"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl クラス

このクラスの既定の実装を提供する、 [ISupportErrorInfo インターフェイス](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)1 つのインターフェイスのみがオブジェクトのエラーを生成するときに使用できます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

#### <a name="parameters"></a>パラメーター

*piid*<br/>
サポートするインターフェイスの IID へのポインター [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)します。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|インターフェイスがで識別されるかどうかを示す`riid`サポート、 [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)インターフェイス。|

## <a name="remarks"></a>Remarks

[ISupportErrorInfo インターフェイス](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)により、クライアントにエラー情報を返されることができます。 使用するオブジェクト`IErrorInfo`実装する必要があります`ISupportErrorInfo`します。

クラス`ISupportErrorInfoImpl`の既定の実装を提供します。 `ISupportErrorInfo` 、1 つのインターフェイスのみがオブジェクトのエラーを生成するときに使用できます。 例:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

インターフェイスがで識別されるかどうかを示す`riid`サポート、 [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)インターフェイス。

```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Remarks

参照してください[ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) Windows SDK にします。

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

プールのスレッドの数を取得するには、このメソッドを呼び出します。

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>パラメーター

*pnNumThreads*<br/>
[out]成功した場合、プールのスレッドの数を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

スレッド プール スレッドをシャット ダウンを待機するミリ秒単位で最大の時刻を取得するには、このメソッドを呼び出します。

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>パラメーター

*pdwMaxWait*<br/>
[out]成功した場合、スレッド プール スレッドをシャット ダウンを待機するミリ秒単位で時間の最大値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="example"></a>例

参照してください[IThreadPoolConfig::GetSize](#getsize)します。

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

プールのスレッドの数を設定するには、このメソッドを呼び出します。

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>パラメーター

*nNumThreads*<br/>
要求されたプール内のスレッド数。

場合*nNumThreads*が負の場合、その絶対値で乗算されますスレッドの合計数を取得するマシンでプロセッサの数。

場合*nNumThreads*ゼロ、ATLS_DEFAULT_THREADSPERPROC はスレッドの合計数を取得するマシンのプロセッサ数が乗算されます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="example"></a>例

参照してください[IThreadPoolConfig::GetSize](#getsize)します。

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

スレッド プール スレッドをシャット ダウンを待機するミリ秒単位で最大の時間を設定するには、このメソッドを呼び出します。

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>パラメーター

*dwMaxWait*<br/>
スレッド プール スレッドをシャット ダウンを待機するミリ秒単位で要求された最大時間。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="example"></a>例

参照してください[IThreadPoolConfig::GetSize](#getsize)します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
