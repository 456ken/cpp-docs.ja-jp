---
title: CComControlBase クラス
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497370"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase クラス

このクラスには、ATL コントロールを作成および管理するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|ストックプロパティが`m_nAppearance` **short**型でない場合は、をオーバーライドします。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|コンストラクターです。|
|[CComControlBase:: ~ CComControlBase](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComControlBase:: ControlQueryInterface](#controlqueryinterface)|要求されたインターフェイスへのポインターを取得します。|
|[CComControlBase::D oesVerbActivate](#doesverbactivate)|に`IOleObjectImpl::DoVerb`よって使用される*iverb*パラメーターがコントロールのユーザーインターフェイス (*iverb* equals OLEIVERB_UIACTIVATE) をアクティブ化することを確認し、ユーザーがコントロールをダブルクリックしたときに実行されるアクションを定義します (*iverb*は OLEIVERB_ になります)。[プライマリ])、コントロール (*Iverb*が OLEIVERB_SHOW) を表示するか、コントロール (*IVERB* equals OLEIVERB_INPLACEACTIVATE) をアクティブにします。|
|[CComControlBase::D oesVerbUIActivate](#doesverbuiactivate)|によって使用される*iverb*パラメーターによって`IOleObjectImpl::DoVerb` 、コントロールのユーザーインターフェイスのアクティブ化が行われ、TRUE が返されることを確認します。|
|[CComControlBase::D oVerbProperties](#doverbproperties)|コントロールのプロパティページを表示します。|
|[CComControlBase::FireViewChange](#fireviewchange)|このメソッドを呼び出して、コントロールを再描画するようにコンテナーに指示します。または、コントロールのビューが変更されたことを登録されたアドバイズシンクに通知します。|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|コントロールの現在の外観の設定である DISPID_AMBIENT_APPEARANCE を取得します。フラットの場合は0、3D の場合は1。|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|コンテナーがコントロールの表示領域の自動クリッピングをサポートするかどうかを示すフラグである DISPID_AMBIENT_AUTOCLIP を取得します。|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|コンテナーによって定義された、すべてのコントロールのアンビエント背景色である DISPID_AMBIENT_BACKCOLOR を取得します。|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|コンテナーで定義されているすべてのコントロールのアンビエント文字セットである DISPID_AMBIENT_CHARSET を取得します。|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|コンテナーで定義されているすべてのコントロールのアンビエント文字セットである DISPID_AMBIENT_CODEPAGE を取得します。|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|DISPID_AMBIENT_DISPLAYASDEFAULT を取得します。このフラグは、コンテナーがこのサイトのコントロールを既定のボタンとしてマークしている場合に TRUE になります。したがって、ボタンコントロールは、フレームを太くして描画する必要があります。|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|コンテナーがコントロールに指定した名前である DISPID_AMBIENT_DISPLAYNAME を取得します。|
|[CComControlBase::GetAmbientFont](#getambientfont)|コンテナーのアンビエント`IFont`インターフェイスへのポインターを取得します。|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|コンテナーのアンビエント`IFontDisp`ディスパッチインターフェイスへのポインターを取得します。|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|コンテナーで定義されているすべてのコントロールのアンビエント前景色である DISPID_AMBIENT_FORECOLOR を取得します。|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|コンテナーによって使用される言語の識別子である DISPID_AMBIENT_LOCALEID を取得します。|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|コンテナーがウィンドウメッセージ (WM_DRAWITEM など) をイベントとして受信するかどうかを示すフラグ (DISPID_AMBIENT_MESSAGEREFLECT) を取得します。|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|コンテナーの HPALETTE にアクセスするために使用される DISPID_AMBIENT_PALETTE を取得します。|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|*Id*で指定されたコンテナープロパティを取得します。|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|コンテナーがコンテンツを表示する方向である DISPID_AMBIENT_RIGHTTOLEFT を取得します。|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|ラベルを表示するためのコンテナーのアンビエント単位 (インチやセンチメートルなど) を DISPID_AMBIENT_SCALEUNITS を取得します。|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|DISPID_AMBIENT_SHOWGRABHANDLES を取得します。このフラグは、アクティブなときに、コンテナーがコントロールにグラブハンドルを表示できるかどうかを示します。|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|UI がアクティブになっているときに、コンテナーでコントロールにハッチパターンを表示させることを許可するかどうかを示すフラグを取得します。このフラグは DISPID_AMBIENT_SHOWHATCHING を取得します。|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|コンテナーでキーボードニーモニックがサポートされているかどうかを示すフラグである DISPID_AMBIENT_SUPPORTSMNEMONICS を取得します。|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|コンテナーで推奨されているテキストの配置を DISPID_AMBIENT_TEXTALIGN を取得します。一般的な配置の場合は0、左揃えの場合は1、中央揃えの場合は2、右揃えの場合は3になります。|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|コンテナーがコンテンツを表示する方向である DISPID_AMBIENT_TOPTOBOTTOM を取得します。|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|DISPID_AMBIENT_UIDEAD を取得します。これは、コンテナーがユーザーインターフェイスの操作に応答するためにコントロールを必要とするかどうかを示すフラグです。|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|コンテナーが実行モード (TRUE) であるか、またはデザインモードである (FALSE) かを示すフラグである DISPID_AMBIENT_USERMODE を取得します。|
|[CComControlBase:: GetDirty](#getdirty)|データメンバー `m_bRequiresSave`の値を返します。|
|[CComControlBase::GetZoomInfo](#getzoominfo)|埋め込み先編集のためにアクティブになっているコントロールについて、分子と分母の x 値と y 値を取得します。|
|[CComControlBase:: Inplace Activate](#inplaceactivate)|コントロールを非アクティブ状態から*Iverb*の動詞が示す任意の状態に遷移させます。|
|[CComControlBase:: InternalGetSite](#internalgetsite)|このメソッドを呼び出して、識別されたインターフェイスへのポインターをコントロールサイトに照会します。|
|[CComControlBase:: OnDraw](#ondraw)|コントロールを描画するには、このメソッドをオーバーライドします。|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|既定`OnDrawAdvanced`では、描画用に正規化されたデバイスコンテキストを準備し`OnDraw`てから、コントロールクラスのメソッドを呼び出します。|
|[CComControlBase::OnKillFocus](#onkillfocus)|コントロールがアクティブであり、有効なコントロールサイトがあることを確認してから、コントロールがフォーカスを失ったことをコンテナーに通知します。|
|[CComControlBase:: OnMouseActivate](#onmouseactivate)|UI がユーザーモードであることを確認してから、コントロールをアクティブにします。|
|[CComControlBase:: OnPaint](#onpaint)|描画するコンテナーを準備し、コントロールのクライアント領域を取得して、コントロールクラスの`OnDraw`メソッドを呼び出します。|
|[CComControlBase:: OnSetFocus](#onsetfocus)|コントロールがアクティブであり、有効なコントロールサイトがあることを確認してから、コントロールがフォーカスを取得したことをコンテナーに通知します。|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|独自のキーボードアクセスハンドラーを提供するには、このメソッドをオーバーライドします。|
|[CComControlBase:: SendOnClose](#sendonclose)|コントロールが閉じられたことを、アドバイズ保持者に登録されているすべてのアドバイズシンクに通知します。|
|[CComControlBase:: SendOnDataChange](#sendondatachange)|コントロールデータが変更されたことをアドバイズホルダーに登録されているすべてのアドバイズシンクに通知します。|
|[CComControlBase:: SendOnRename](#sendonrename)|コントロールに新しいモニカーがあることを、アドバイズホルダーに登録されているすべてのアドバイズシンクに通知します。|
|[CComControlBase:: SendOnSave](#sendonsave)|コントロールが保存されたことを、アドバイズ保持者に登録されているすべてのアドバイズシンクに通知します。|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|コントロールのビューが変更されたことを、登録されているすべてのアドバイズシンクに通知します。|
|[CComControlBase:: SetControlFocus](#setcontrolfocus)|コントロールとの間でキーボードフォーカスを設定または削除します。|
|[CComControlBase:: SetDirty](#setdirty)|データメンバー `m_bRequiresSave`を*bdirty*の値に設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|コントロールを他のサイズにすることができないことを示すフラグ。|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|と`IDataObjectImpl::GetData` `m_sizeNatural`ではなく、コントロールの`m_sizeExtent`サイズをに設定する必要があることを示すフラグ。 `CComControlBase::GetZoomInfo`|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|描画するとき`IDataObjectImpl::GetData`に、が HIMETRIC 単位を使用する必要があることを示すフラグ。|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|コントロールがアクティブな状態であることを示すフラグ。|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|コンテナーが、ウィンドウなしや`IOleInPlaceSiteEx`ちらつきなしのコントロールなどのインターフェイスおよび OCX96 コントロール機能をサポートしていることを示すフラグ。|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|コントロールが、OCX96 コントロール機能 (ちらつきなし、ウィンドウなしのコントロールなど) のサポートについてコンテナーとネゴシエートしたかどうか、およびコントロールがウィンドウかウィンドウなしかを示すフラグです。|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|コンテナーがコントロールの表示サイズを変更したときに、コントロールがそのプレゼンテーションを再構成することを示すフラグ。|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|コントロールが最後に保存されてから変更されたことを示すフラグ。|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|コンテナーがコントロールの表示サイズを変更したときに、コントロールが自然な範囲 (スケーリングされていない物理サイズ) のサイズを変更しようとしていることを示すフラグ。|
|[CComControlBase::m_bUIActive](#m_buiactive)|メニューやツールバーなど、コントロールのユーザーインターフェイスがアクティブであることを示すフラグ。|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|コントロールがコンテナーによって指定されたウィンドウ領域を使用していることを示すフラグ。|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|コントロールがウィンドウなしで表示されているが、現在はウィンドウなしであることを示すフラグ。|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|コンテナーがウィンドウなしのコントロールをサポートしている場合でも、コントロールをウィンドウにする必要があることを示すフラグ。|
|[CComControlBase::m_bWndLess](#m_bwndless)|コントロールがウィンドウなしであることを示すフラグ。|
|[CComControlBase::m_hWndCD](#m_hwndcd)|コントロールに関連付けられているウィンドウハンドルへの参照を格納します。|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|イベントの凍結解除 (イベントの受理) が発生することなく、コンテナーが凍結されたイベントを持つ (イベントの受け入れを拒否される) 回数のカウント。|
|[CComControlBase::m_rcPos](#m_rcpos)|コンテナーの座標で表される、コントロールのピクセル単位の位置。|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|特定の表示について、HIMETRIC 単位 (各単位は 0.01 mm) のコントロールの範囲。|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|HIMETRIC 単位 (各単位は0.01 ミリメートル) のコントロールの物理サイズ。|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|コンテナーのアドバイザリコネクションへの直接ポインター (コンテナーの[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink))。|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|ポインターを使用してコンテナーのプロパティを取得および設定できるオブジェクト。`CComDispatchDriver` `IDispatch`|
|[CComControlBase::m_spClientSite](#m_spclientsite)|コンテナー内のコントロールのクライアントサイトへのポインター。|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|データオブジェクトとアドバイズシンク間のアドバイザリコネクションを保持するための標準的な手段を提供します。|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|コンテナーの[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)インターフェイスポインターへのポインター。|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|アドバイザリコネクションを保持する手段の標準的な実装を提供します。|

## <a name="remarks"></a>Remarks

このクラスには、ATL コントロールを作成および管理するためのメソッドが用意されています。 [CComControl クラス](../../atl/reference/ccomcontrol-class.md)はから`CComControlBase`派生します。 ATL コントロールウィザードを使用して標準コントロールまたは DHTML コントロールを作成すると、ウィザードによってから`CComControlBase`クラスが自動的に派生されます。

コントロールの作成の詳細については、 [ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)を参照してください。 ATL プロジェクトウィザードの詳細については、「 [Atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

ストックプロパティが`m_nAppearance` **short**型でない場合は、をオーバーライドします。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Remarks

ATL コントロールウィザードでは`m_nAppearance` 、short 型のストックプロパティが追加されます。 別`AppearanceType`のデータ型を使用する場合は、をオーバーライドします。

##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

コンストラクターです。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
コントロールに関連付けられているウィンドウへのハンドル。

### <a name="remarks"></a>Remarks

コントロールサイズを 5080x5080 HIMETRIC 単位 (2 "X2") に初期化し、 `CComControlBase`データメンバー値を NULL または FALSE に初期化します。

##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase

デストラクターです。

```
~CComControlBase();
```

### <a name="remarks"></a>Remarks

コントロールがウィンドウになって`~CComControlBase`いる場合は、 [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow)を呼び出して破棄します。

##  <a name="controlqueryinterface"></a>CComControlBase:: ControlQueryInterface

要求されたインターフェイスへのポインターを取得します。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
要求されているインターフェイスの GUID。

*ppv*<br/>
*Iid*によって識別されるインターフェイスポインターへのポインター。インターフェイスが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

は COM マップテーブル内のインターフェイスのみを処理します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>CComControlBase::D oesVerbActivate

に`IOleObjectImpl::DoVerb`よって使用される*iverb*パラメーターがコントロールのユーザーインターフェイス (*iverb* equals OLEIVERB_UIACTIVATE) をアクティブ化することを確認し、ユーザーがコントロールをダブルクリックしたときに実行されるアクションを定義します (*iverb*は OLEIVERB_ になります)。[プライマリ])、コントロール (*Iverb*が OLEIVERB_SHOW) を表示するか、コントロール (*IVERB* equals OLEIVERB_INPLACEACTIVATE) をアクティブにします。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
によって`DoVerb`実行されるアクションを示す値。

### <a name="return-value"></a>戻り値

*Iverb*が OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW、または OLEIVERB_INPLACEACTIVATE に等しい場合に TRUE を返します。それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドして、独自のアクティブ化動詞を定義できます。

##  <a name="doesverbuiactivate"></a>CComControlBase::D oesVerbUIActivate

によって使用される*iverb*パラメーターによって`IOleObjectImpl::DoVerb` 、コントロールのユーザーインターフェイスのアクティブ化が行われ、TRUE が返されることを確認します。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
によって`DoVerb`実行されるアクションを示す値。

### <a name="return-value"></a>戻り値

*Iverb*が OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW、または OLEIVERB_INPLACEACTIVATE に等しい場合に TRUE を返します。 それ以外の場合、メソッドは FALSE を返します。

##  <a name="doverbproperties"></a>CComControlBase::D oVerbProperties

コントロールのプロパティページを表示します。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>パラメーター

*prcPosRec*<br/>
予約済み。

*hwndParent*<br/>
コントロールを格納しているウィンドウのハンドル。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>CComControlBase::FireViewChange

このメソッドを呼び出して、コントロールを再描画するようにコンテナーに指示します。または、コントロールのビューが変更されたことを登録されたアドバイズシンクに通知します。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールがアクティブな場合 (コントロールクラスのデータメンバー [CComControlBase:: m_bInPlaceActive](#m_binplaceactive)が TRUE の場合)、は、コントロール全体を再描画するようにコンテナーに通知します。 コントロールが非アクティブである場合は、コントロールのビューが変更されたことをコントロールの登録済みのアドバイズシンク (コントロールクラスのデータメンバー [CComControlBase:: m_spAdviseSink](#m_spadvisesink)) に通知します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

コントロールの現在の外観の設定である DISPID_AMBIENT_APPEARANCE を取得します。フラットの場合は0、3D の場合は1。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>パラメーター

*nAppearance*<br/>
プロパティ DISPID_AMBIENT_APPEARANCE。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

コンテナーがコントロールの表示領域の自動クリッピングをサポートするかどうかを示すフラグである DISPID_AMBIENT_AUTOCLIP を取得します。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>パラメーター

*bAutoClip*<br/>
プロパティ DISPID_AMBIENT_AUTOCLIP。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

コンテナーによって定義された、すべてのコントロールのアンビエント背景色である DISPID_AMBIENT_BACKCOLOR を取得します。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
プロパティ DISPID_AMBIENT_BACKCOLOR。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

コンテナーで定義されているすべてのコントロールのアンビエント文字セットである DISPID_AMBIENT_CHARSET を取得します。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>パラメーター

*bstrCharSet*<br/>
プロパティ DISPID_AMBIENT_CHARSET。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

コンテナーで定義されているすべてのコントロールのアンビエントコードページである DISPID_AMBIENT_CODEPAGE を取得します。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>パラメーター

*ulCodePage*<br/>
プロパティ DISPID_AMBIENT_CODEPAGE。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

DISPID_AMBIENT_DISPLAYASDEFAULT を取得します。このフラグは、コンテナーがこのサイトのコントロールを既定のボタンとしてマークしている場合に TRUE になります。したがって、ボタンコントロールは、フレームを太くして描画する必要があります。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>パラメーター

*bDisplayAsDefault*<br/>
プロパティ DISPID_AMBIENT_DISPLAYASDEFAULT。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

コンテナーがコントロールに指定した名前である DISPID_AMBIENT_DISPLAYNAME を取得します。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>パラメーター

*bstrDisplayName*<br/>
プロパティ DISPID_AMBIENT_DISPLAYNAME。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

コンテナーのアンビエント`IFont`インターフェイスへのポインターを取得します。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>パラメーター

*ppFont*<br/>
コンテナーのアンビエント[IFont](/windows/win32/api/ocidl/nn-ocidl-ifont)インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

プロパティが NULL の場合、ポインターは NULL になります。 ポインターが NULL でない場合、呼び出し元はポインターを解放する必要があります。

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

コンテナーのアンビエント`IFontDisp`ディスパッチインターフェイスへのポインターを取得します。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>パラメーター

*ppFont*<br/>
コンテナーのアンビエント[IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp)ディスパッチインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

プロパティが NULL の場合、ポインターは NULL になります。 ポインターが NULL でない場合、呼び出し元はポインターを解放する必要があります。

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

コンテナーで定義されているすべてのコントロールのアンビエント前景色である DISPID_AMBIENT_FORECOLOR を取得します。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>パラメーター

*景色*<br/>
プロパティ DISPID_AMBIENT_FORECOLOR。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

コンテナーによって使用される言語の識別子である DISPID_AMBIENT_LOCALEID を取得します。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>パラメーター

*lcid*<br/>
プロパティ DISPID_AMBIENT_LOCALEID。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールはこの識別子を使用して、ユーザーインターフェイスを異なる言語に適合させることができます。

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

コンテナーがウィンドウメッセージ (など`WM_DRAWITEM`) をイベントとして受信するかどうかを示すフラグ (DISPID_AMBIENT_MESSAGEREFLECT) を取得します。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>パラメーター

*bMessageReflect*<br/>
プロパティ DISPID_AMBIENT_MESSAGEREFLECT。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

コンテナーの HPALETTE にアクセスするために使用される DISPID_AMBIENT_PALETTE を取得します。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>パラメーター

*hPalette*<br/>
プロパティ DISPID_AMBIENT_PALETTE。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

*Dispid*によって指定されたコンテナープロパティを取得します。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
取得するコンテナープロパティの識別子。

*var*<br/>
プロパティを受け取る変数。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

ATL には、 [CComControlBase:: GetAmbientBackColor](#getambientbackcolor)などの特定のプロパティを取得するためのヘルパー関数のセットが用意されています。 使用できる適切な方法がない場合は`GetAmbientProperty`、を使用します。

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

コンテナーがコンテンツを表示する方向である DISPID_AMBIENT_RIGHTTOLEFT を取得します。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>パラメーター

*bRightToLeft*<br/>
プロパティ DISPID_AMBIENT_RIGHTTOLEFT。 コンテンツが右から左に表示される場合は TRUE に、左から右に表示される場合は FALSE に設定されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

ラベルを表示するためのコンテナーのアンビエント単位 (インチやセンチメートルなど) を DISPID_AMBIENT_SCALEUNITS を取得します。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>パラメーター

*bstrScaleUnits*<br/>
プロパティ DISPID_AMBIENT_SCALEUNITS。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

DISPID_AMBIENT_SHOWGRABHANDLES を取得します。このフラグは、アクティブなときに、コンテナーがコントロールにグラブハンドルを表示できるかどうかを示します。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>パラメーター

*bShowGrabHandles*<br/>
プロパティ DISPID_AMBIENT_SHOWGRABHANDLES。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

コントロールのユーザーインターフェイスがアクティブになっている場合に、コントロールがコントロールにハッチパターンで表示されることを許可するかどうかを示すフラグである DISPID_AMBIENT_SHOWHATCHING を取得します。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>パラメーター

*Bshoは、*<br/>
プロパティ DISPID_AMBIENT_SHOWHATCHING。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

コンテナーでキーボードニーモニックがサポートされているかどうかを示すフラグである DISPID_AMBIENT_SUPPORTSMNEMONICS を取得します。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>パラメーター

*Bsupportsmnている Ics*<br/>
プロパティ DISPID_AMBIENT_SUPPORTSMNEMONICS。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

コンテナーで推奨されているテキストの配置を DISPID_AMBIENT_TEXTALIGN を取得します。一般的な配置の場合は0、左揃えの場合は1、中央揃えの場合は2、右揃えの場合は3になります。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>パラメーター

*nTextAlign*<br/>
プロパティ DISPID_AMBIENT_TEXTALIGN。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

コンテナーがコンテンツを表示する方向である DISPID_AMBIENT_TOPTOBOTTOM を取得します。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>パラメーター

*bTopToBottom*<br/>
プロパティ DISPID_AMBIENT_TOPTOBOTTOM。 テキストが上から下に表示される場合は TRUE に設定され、下から上に表示される場合は FALSE に設定されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

DISPID_AMBIENT_UIDEAD を取得します。これは、コンテナーがユーザーインターフェイスの操作に応答するためにコントロールを必要とするかどうかを示すフラグです。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>パラメーター

*Buide Ad*<br/>
プロパティ DISPID_AMBIENT_UIDEAD。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

TRUE の場合、コントロールは応答しません。 このフラグは、DISPID_AMBIENT_USERMODE フラグに関係なく適用されます。 「 [CComControlBase:: GetAmbientUserMode](#getambientusermode)」を参照してください。

##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

コンテナーが実行モード (TRUE) であるか、またはデザインモードである (FALSE) かを示すフラグである DISPID_AMBIENT_USERMODE を取得します。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>パラメーター

*bUserMode*<br/>
プロパティ DISPID_AMBIENT_USERMODE。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="getdirty"></a>CComControlBase:: GetDirty

データメンバー `m_bRequiresSave`の値を返します。

```
BOOL GetDirty();
```

### <a name="return-value"></a>戻り値

データメンバー [m_bRequiresSave](#m_brequiressave)の値を返します。

### <a name="remarks"></a>Remarks

この値は[CComControlBase:: SetDirty](#setdirty)を使用して設定されます。

##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo

埋め込み先編集のためにアクティブになっているコントロールについて、分子と分母の x 値と y 値を取得します。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>パラメーター

*di*<br/>
ズームファクターの分子と分母を保持する構造体。 詳細については、「 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)」を参照してください。

### <a name="remarks"></a>Remarks

ズーム率は、現在の範囲に対するコントロールの自然サイズの比率です。

##  <a name="inplaceactivate"></a>CComControlBase:: Inplace Activate

コントロールを非アクティブ状態から*Iverb*の動詞が示す任意の状態に遷移させます。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
[IOleObjectImpl::D oVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)によって実行されるアクションを示す値。

*prcPosRect*<br/>
インプレースコントロールの位置へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

アクティベーションの前に、このメソッドはコントロールにクライアントサイトがあることを確認し、コントロールの表示範囲を確認し、親ウィンドウ内のコントロールの位置を取得します。 コントロールがアクティブになると、このメソッドはコントロールのユーザーインターフェイスをアクティブにし、コントロールを表示するようにコンテナーに指示します。

また、このメソッドは`IOleInPlaceSite`、 `IOleInPlaceSiteEx`コントロールの`IOleInPlaceSiteWindowless` 、、またはの各インターフェイスポインターを取得し、コントロールクラスのデータメンバー [CComControlBase:: m_spInPlaceSite](#m_spinplacesite)に格納します。 必要に応じて、コントロールクラスのデータメンバー [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)、 [CComControlBase:: m_bWndLess](#m_bwndless)、 [CComControlBase:: m_bWasOnceWindowless](#m_bwasoncewindowless)、および[CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)が true に設定されます。

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

このメソッドを呼び出して、識別されたインターフェイスへのポインターをコントロールサイトに照会します。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
*PpUnkSite*で返されるインターフェイスポインターの IID。

*ppUnkSite*<br/>
*Riid*で要求されたインターフェイスポインターを受け取るポインター変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

サイトが、 *riid*で要求されたインターフェイスをサポートしている場合は、 *ppUnkSite*によってポインターが返されます。 それ以外の場合、 *ppUnkSite*は NULL に設定されます。

##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize

コントロールを他のサイズにすることができないことを示すフラグ。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Remarks

このフラグはによっ`IOleObjectImpl::SetExtent`てチェックされ、TRUE の場合、関数は E_FAIL を返します。

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

ATL コントロールウィザードの [[ストックのプロパティ](../../atl/reference/stock-properties-atl-control-wizard.md)] タブで **[自動サイズ]** オプションを追加すると、ウィザードは自動的にこのデータメンバーをコントロールクラスに作成し、プロパティの put メソッドと get メソッドを作成して、[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) をサポートします。プロパティが変更されたときにコンテナーに自動的に通知する場合は。

##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

と`IDataObjectImpl::GetData` `m_sizeNatural`ではなく、コントロールの`m_sizeExtent`サイズをに設定する必要があることを示すフラグ。 `CComControlBase::GetZoomInfo`

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

描画するとき`IDataObjectImpl::GetData`に、が HIMETRIC 単位を使用する必要があることを示すフラグ。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Remarks

各論理 HIMETRIC 単位は0.01 ミリメートルです。

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive

コントロールがアクティブな状態であることを示すフラグ。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Remarks

これは、コントロールが表示され、ウィンドウがある場合はそのウィンドウが表示されることを意味しますが、そのメニューとツールバーはアクティブにならない可能性があります。 フラグ`m_bUIActive`は、メニューなどのコントロールのユーザーインターフェイスもアクティブであることを示します。

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

コンテナーが、ウィンドウなしや`IOleInPlaceSiteEx`ちらつきなしのコントロールなどのインターフェイスおよび OCX96 コントロール機能をサポートしていることを示すフラグ。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

`m_spInPlaceSite`データメンバー `m_bWndLess`は、フラグとフラグの値に応じて、[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) インターフェイスを指し`m_bInPlaceSiteEx`ます。 (ポインターが`m_spInPlaceSite`有効`m_bNegotiatedWnd`であるためには、データメンバーが TRUE である必要があります)。

が`m_bWndLess` FALSE で`m_bInPlaceSiteEx` あり、`m_spInPlaceSite`が TRUE の場合、はインターフェイスポインターです。`IOleInPlaceSiteEx` これら3つのデータメンバー間の関係を示す表については、「 [m_spInPlaceSite](#m_spinplacesite) 」を参照してください。

##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

コントロールが、OCX96 コントロール機能 (ちらつきなし、ウィンドウなしのコントロールなど) のサポートについてコンテナーとネゴシエートしたかどうか、およびコントロールがウィンドウかウィンドウなしかを示すフラグです。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

`m_spInPlaceSite`ポインターが有効であるためには、 `m_bNegotiatedWnd`フラグが TRUE である必要があります。

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

コンテナーがコントロールの表示サイズを変更したときに、コントロールがそのプレゼンテーションを再構成することを示すフラグ。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

このフラグは[IOleObjectImpl:: setextent](../../atl/reference/ioleobjectimpl-class.md#setextent)によってチェックされ、 `SetExtent` TRUE の場合は、ビューの変更をコンテナーに通知します。 このフラグが設定されている場合は、 [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)列挙の OLEMISC_RECOMPOSEONRESIZE ビットも設定する必要があります。

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

コントロールが最後に保存されてから変更されたことを示すフラグ。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Remarks

の`m_bRequiresSave`値は[CComControlBase:: setdirty](#setdirty)で設定でき、 [CComControlBase:: getdirty](#getdirty)を使用して取得されます。

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

コンテナーがコントロールの表示サイズを変更したときに、コントロールが自然な範囲 (スケーリングされていない物理サイズ) のサイズを変更しようとしていることを示すフラグ。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Remarks

このフラグはによっ`IOleObjectImpl::SetExtent`てチェックされ、TRUE の場合、 `SetExtent`に渡される`m_sizeNatural`サイズはに割り当てられます。

に`SetExtent`渡されるサイズは、の`m_bResizeNatural`値`m_sizeExtent`に関係なく、常にに割り当てられます。

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive

メニューやツールバーなど、コントロールのユーザーインターフェイスがアクティブであることを示すフラグ。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Remarks

`m_bInPlaceActive`フラグは、コントロールがアクティブであることを示しますが、そのユーザーインターフェイスがアクティブであることを示します。

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

コントロールがコンテナーによって指定されたウィンドウ領域を使用していることを示すフラグ。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

コントロールがウィンドウなしで表示されているが、現在はウィンドウなしであることを示すフラグ。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

コンテナーがウィンドウなしのコントロールをサポートしている場合でも、コントロールをウィンドウにする必要があることを示すフラグ。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess

コントロールがウィンドウなしであることを示すフラグ。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

`m_spInPlaceSite`データメンバーは、および [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) フラグの値に応じて、[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) インターフェイス`m_bWndLess`を指します。 ( [CComControlBase:: m_spInPlaceSite](#m_spinplacesite)ポインターが有効であるためには、データメンバー [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)が TRUE である必要があります)。

が`m_bWndLess` TRUE の場合`m_spInPlaceSite` 、は`IOleInPlaceSiteWindowless`インターフェイスポインターです。 これらのデータメンバーの間の完全なリレーションシップを示す表については、「 [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) 」を参照してください。

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

コントロールに関連付けられているウィンドウハンドルへの参照を格納します。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

イベントの凍結解除 (イベントの受理) が発生することなく、コンテナーが凍結されたイベントを持つ (イベントの受け入れを拒否される) 回数のカウント。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_rcpos"></a>CComControlBase::m_rcPos

コンテナーの座標で表される、コントロールのピクセル単位の位置。

```
RECT m_rcPos;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

特定の表示について、HIMETRIC 単位 (各単位は 0.01 mm) のコントロールの範囲。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

このサイズは、表示によって拡大縮小されます。 コントロールの物理サイズは`m_sizeNatural`データメンバーで指定され、固定されています。

グローバル関数の[Atlhimetrictopixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)を使用して、サイズをピクセルに変換することができます。

##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

HIMETRIC 単位 (各単位は0.01 ミリメートル) のコントロールの物理サイズ。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

このサイズは固定されています`m_sizeExtent`が、のサイズはディスプレイによってスケーリングされます。

グローバル関数の[Atlhimetrictopixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)を使用して、サイズをピクセルに変換することができます。

##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

コンテナーのアドバイザリコネクションへの直接ポインター (コンテナーの[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink))。

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

オブジェクトのプロパティを取得し、 `IDispatch`ポインターを介して設定できるオブジェクト。`CComDispatchDriver`

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite

コンテナー内のコントロールのクライアントサイトへのポインター。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

データオブジェクトとアドバイズシンク間のアドバイザリコネクションを保持するための標準的な手段を提供します。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

データオブジェクトは、データを転送できるコントロールであり、データの形式と転送メディアを指定するメソッドを持つ[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)を実装します。

このインターフェイス`m_spDataAdviseHolder`は、コンテナーへのアドバイザリコネクションを確立および削除するための[IDataObject::D advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)と[IDataObject::D のアドバイズ](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)メソッドを実装します。 コントロールのコンテナーは、 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)インターフェイスをサポートすることにより、アドバイズシンクを実装する必要があります。

##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

コンテナーの[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)インターフェイスポインターへのポインター。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

ポインターは、[m_bNegotiatedWnd](#m_bnegotiatedwnd) フラグが TRUE の場合にのみ有効です。`m_spInPlaceSite`

次の表は、ポインター `m_spInPlaceSite`型がどのように[m_bWndLess](#m_bwndless)および[m_bInPlaceSiteEx](#m_binplacesiteex)データメンバーフラグに依存しているかを示しています。

|m_spInPlaceSite 型|m_bWndLess 値|m_bInPlaceSiteEx 値|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|TRUE または FALSE|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

アドバイザリコネクションを保持する手段の標準的な実装を提供します。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールクラス内でこのデータメンバーを使用するには、コントロールクラスのデータメンバーとして宣言する必要があります。 コントロールクラスは、基底クラスの共用体で宣言されているため、基底クラスからこのデータメンバーを継承しません。

インターフェイス`m_spOleAdviseHolder`は、コンテナーへのアドバイザリコネクションを確立および削除するための[IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)メソッドと[IOleObject:: アドバイズ](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)メソッドを実装します。 コントロールのコンテナーは、 [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)インターフェイスをサポートすることにより、アドバイズシンクを実装する必要があります。

##  <a name="ondraw"></a>CComControlBase:: OnDraw

コントロールを描画するには、このメソッドをオーバーライドします。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>パラメーター

*di*<br/>
描画のアスペクト、コントロールの境界、描画が最適化されているかどうかなどの描画情報を格納する[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)構造体への参照。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

既定`OnDraw`では、 [CComControlBase:: OnDrawAdvanced](#ondrawadvanced)に設定されているフラグに応じて、デバイスコンテキストが削除または復元されるか、何も実行されません。

ATL コントロールウィザードを使用してコントロールを作成すると、コントロールクラスにメソッドが自動的に追加されます。`OnDraw` ウィザードの既定`OnDraw`では、"ATL 8.0" というラベルの四角形が描画されます。

### <a name="example"></a>例

[CComControlBase:: GetAmbientAppearance](#getambientappearance)の例を参照してください。

##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

既定`OnDrawAdvanced`では、描画用に正規化されたデバイスコンテキストを準備し`OnDraw`てから、コントロールクラスのメソッドを呼び出します。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>パラメーター

*di*<br/>
描画のアスペクト、コントロールの境界、描画が最適化されているかどうかなどの描画情報を格納する[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)構造体への参照。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

このメソッドは、正規化せずにコンテナーによって渡されたデバイスコンテキストを受け入れる場合にオーバーライドします。

詳細については、「 [CComControlBase:: OnDraw](#ondraw) 」を参照してください。

##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus

コントロールがアクティブであり、有効なコントロールサイトがあることを確認してから、コントロールがフォーカスを失ったことをコンテナーに通知します。

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
予約済み。

*lParam*<br/>
予約済み。

*bHandled*<br/>
ウィンドウメッセージが正常に処理されたかどうかを示すフラグ。 既定値は FALSE です。

### <a name="return-value"></a>戻り値

常に1を返します。

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

UI がユーザーモードであることを確認してから、コントロールをアクティブにします。

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
予約済み。

*lParam*<br/>
予約済み。

*bHandled*<br/>
ウィンドウメッセージが正常に処理されたかどうかを示すフラグ。 既定値は FALSE です。

### <a name="return-value"></a>戻り値

常に1を返します。

##  <a name="onpaint"></a>  CComControlBase::OnPaint

描画するコンテナーを準備し、コントロールのクライアント領域を取得して、コントロールクラスの`OnDrawAdvanced`メソッドを呼び出します。

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
既存の HDC。

*lParam*<br/>
予約済み。

*lResult*<br/>
予約済み。

### <a name="return-value"></a>戻り値

常に0を返します。

### <a name="remarks"></a>Remarks

*WParam*が NULL でない場合`OnPaint` 、は有効な HDC を含んでいると想定し、 [CComControlBase:: m_hWndCD](#m_hwndcd)の代わりにそれを使用します。

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

コントロールがアクティブであり、有効なコントロールサイトがあることを確認してから、コントロールがフォーカスを取得したことをコンテナーに通知します。

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
予約済み。

*lParam*<br/>
予約済み。

*bHandled*<br/>
ウィンドウメッセージが正常に処理されたかどうかを示すフラグ。 既定値は FALSE です。

### <a name="return-value"></a>戻り値

常に1を返します。

### <a name="remarks"></a>Remarks

コントロールがフォーカスを受け取ったコンテナーに通知を送信します。

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

独自のキーボードアクセスハンドラーを提供するには、このメソッドをオーバーライドします。

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
予約済み。

*hRet*<br/>
予約済み。

### <a name="return-value"></a>戻り値

既定では FALSE が返されます。

##  <a name="sendonclose"></a>CComControlBase:: SendOnClose

コントロールが閉じられたことを、アドバイズ保持者に登録されているすべてのアドバイズシンクに通知します。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

コントロールがアドバイズシンクを閉じたことを示す通知を送信します。

##  <a name="sendondatachange"></a>CComControlBase:: SendOnDataChange

コントロールデータが変更されたことをアドバイズホルダーに登録されているすべてのアドバイズシンクに通知します。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>パラメーター

*advf*<br/>
[IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange)の呼び出しを行う方法を指定するアドバイズフラグ。 値は[ADVF](/windows/win32/api/objidl/ne-objidl-advf)列挙体からの値です。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="sendonrename"></a>CComControlBase:: SendOnRename

コントロールに新しいモニカーがあることを、アドバイズホルダーに登録されているすべてのアドバイズシンクに通知します。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>パラメーター

*time*<br/>
コントロールの新しいモニカーへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

コントロールのモニカーが変更されたことを示す通知を送信します。

##  <a name="sendonsave"></a>CComControlBase:: SendOnSave

コントロールが保存されたことを、アドバイズ保持者に登録されているすべてのアドバイズシンクに通知します。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

コントロールがデータを保存したばかりの通知を送信します。

##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

コントロールのビューが変更されたことを、登録されているすべてのアドバイズシンクに通知します。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>パラメーター

*dwAspect*<br/>
コントロールの縦横またはビュー。

*lindex*<br/>
ビューの変更された部分。 有効なのは-1 だけです。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

`SendOnViewChange`[IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)を呼び出します。 現在サポートされている*lindex*の唯一の値は-1 です。これは、ビュー全体が対象であることを示します。

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

コントロールとの間でキーボードフォーカスを設定または削除します。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>パラメーター

*bGrab*<br/>
TRUE の場合、キーボードフォーカスを呼び出し元のコントロールに設定します。 FALSE の場合、フォーカスがある場合は、呼び出し元のコントロールからキーボードフォーカスを削除します。

### <a name="return-value"></a>戻り値

コントロールがフォーカスを正常に受信した場合は TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ウィンドウコントロールの場合は、Windows API 関数[SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus)が呼び出されます。 ウィンドウなしのコントロールでは、 [IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus)が呼び出されます。 この呼び出しにより、ウィンドウなしのコントロールがキーボードフォーカスを取得し、ウィンドウメッセージに応答できるようになります。

##  <a name="setdirty"></a>CComControlBase:: SetDirty

データメンバー `m_bRequiresSave`を*bdirty*の値に設定します。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>パラメーター

*bDirty*<br/>
データメンバー [CComControlBase:: m_bRequiresSave](#m_brequiressave)の値。

### <a name="remarks"></a>Remarks

`SetDirty(TRUE)`コントロールが最後に保存されてから変更されたことを示すフラグを付けるには、を呼び出す必要があります。 の`m_bRequiresSave`値は[CComControlBase:: getdirty](#getdirty)を使用して取得されます。

## <a name="see-also"></a>関連項目

[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
