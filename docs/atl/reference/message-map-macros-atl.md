---
title: メッセージマップマクロ (ATL)
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 42fdc7a3f09568b641229e897a2a493994a7ba8a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495357"
---
# <a name="message-map-macros-atl"></a>メッセージマップマクロ (ATL)

これらのマクロは、メッセージマップとエントリを定義します。

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|代替メッセージマップの開始をマークします。|
|[BEGIN_MSG_MAP](#begin_msg_map)|既定のメッセージマップの開始をマークします。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|基底クラスの代替メッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|クラスのデータメンバー内の代替メッセージマップにチェーンします。|
|[CHAIN_MSG_MAP](#chain_msg_map)|基本クラスの既定のメッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|実行時に別のクラスのメッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|クラスのデータメンバーの既定のメッセージマップにチェーンします。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|通知コードに基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_HANDLER](#command_handler)|通知コードと、メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_ID_HANDLER](#command_id_handler)|メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|通知コードと、コントロール id の連続する範囲に基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|コントロール id の連続した範囲に基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|空のメッセージマップを実装します。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|それ以外の処理を行わない、リフレクションされたメッセージの既定のハンドラーを提供します。|
|[END_MSG_MAP](#end_msg_map)|メッセージマップの終了をマークします。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|通知メッセージを親ウィンドウに転送します。|
|[MESSAGE_HANDLER](#message_handler)|Windows メッセージをハンドラー関数にマップします。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Windows メッセージの連続する範囲をハンドラー関数にマップします。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|は、通知コードに基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_HANDLER](#notify_handler)|は、通知コードおよびコントロール識別子に基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|コントロール識別子に基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|は、通知コードと、コントロール id の連続する範囲に基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|コントロール id の連続した範囲に基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|は、通知メッセージを送信したウィンドウに返信します。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|通知コードに基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|通知コードとメニュー項目、コントロール、またはアクセラレータの識別子に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|通知コードと、コントロール id の連続する範囲に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|制御識別子の連続した範囲に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|通知コードに基づいて、反映された WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|通知コードとコントロール識別子に基づいて、リフレクションされた WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|コントロール識別子に基づいて、リフレクションされた WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|リフレクションされた WM_NOTIFY メッセージを、通知コードと、コントロール id の連続する範囲に基づいてハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|コントロール識別子の連続する範囲に基づいて、リフレクションされた WM_NOTIFY メッセージをハンドラー関数にマップします。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="alt_msg_map"></a>ALT_MSG_MAP

代替メッセージマップの開始をマークします。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>パラメーター

*msgMapID*<br/>
からメッセージマップの識別子。

### <a name="remarks"></a>Remarks

ATL では、各メッセージマップを数値で識別します。 既定のメッセージマップ (BEGIN_MSG_MAP マクロで宣言) は0で識別されます。 代替メッセージマップは、 *Msgmapid*によって識別されます。

メッセージマップは、ウィンドウに送信されたメッセージを処理するために使用されます。 たとえば、 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)を使用すると、親オブジェクト内のメッセージマップの識別子を指定できます。 [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc)は、このメッセージマップを使用して、含まれているウィンドウのメッセージを適切なハンドラー関数または別のメッセージマップに送信します。 ハンドラー関数を宣言するマクロの一覧については、「 [BEGIN_MSG_MAP](#begin_msg_map)」を参照してください。

常に BEGIN_MSG_MAP を使用してメッセージマップを開始します。 その後、後続の代替メッセージマップを宣言できます。

[END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 BEGIN_MSG_MAP と END_MSG_MAP のインスタンスは常に1つだけであることに注意してください。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="example"></a>例

次の例は、既定のメッセージマップと1つの代替メッセージマップを示しています。それぞれに1つのハンドラー関数が含まれています。

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

次の例では、2つの代替メッセージマップを示します。 既定のメッセージマップが空です。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP

既定のメッセージマップの開始をマークします。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
からメッセージマップを格納しているクラスの名前。

### <a name="remarks"></a>Remarks

[CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc)は、既定のメッセージマップを使用して、ウィンドウに送信されたメッセージを処理します。 メッセージマップは、適切なハンドラー関数または別のメッセージマップにメッセージを送信します。

次のマクロは、メッセージをハンドラー関数にマップします。 この関数は、*クラス*で定義されている必要があります。

|マクロ|説明|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Windows メッセージをハンドラー関数にマップします。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Windows メッセージの連続する範囲をハンドラー関数にマップします。|
|[COMMAND_HANDLER](#command_handler)|通知コードと、メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_ID_HANDLER](#command_id_handler)|メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_CODE_HANDLER](#command_handler)|通知コードに基づいて、WM_COMMAND メッセージをハンドラー関数にマップします。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、WM_COMMAND メッセージの連続する範囲をハンドラー関数にマップします。|
|[NOTIFY_HANDLER](#notify_handler)|は、通知コードおよびコントロール識別子に基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|コントロール識別子に基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|は、通知コードに基づいて、WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|コントロール識別子に基づいて、WM_NOTIFY メッセージの連続した範囲をハンドラー関数にマップします。|

次のマクロは、メッセージを別のメッセージマップに転送します。 このプロセスは "チェーン" と呼ばれます。

|マクロ|説明|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|基本クラスの既定のメッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|クラスのデータメンバーの既定のメッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|基底クラスの代替メッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|クラスのデータメンバー内の代替メッセージマップにチェーンします。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|実行時に別のクラスの既定のメッセージマップにチェーンします。|

次のマクロは、親ウィンドウから "リフレクション" メッセージをダイレクトします。 たとえば、コントロールは通常、通知メッセージを処理のために親ウィンドウに送信しますが、親ウィンドウはそのメッセージをコントロールに反映させることができます。

|マクロ|説明|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|通知コードとメニュー項目、コントロール、またはアクセラレータの識別子に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|メニュー項目、コントロール、またはアクセラレータの識別子に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|通知コードに基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|制御識別子の連続した範囲に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|通知コードと、コントロール id の連続する範囲に基づいて、リフレクションされた WM_COMMAND メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|通知コードとコントロール識別子に基づいて、リフレクションされた WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|コントロール識別子に基づいて、リフレクションされた WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|通知コードに基づいて、反映された WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|コントロール識別子の連続する範囲に基づいて、リフレクションされた WM_NOTIFY メッセージをハンドラー関数にマップします。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|リフレクションされた WM_NOTIFY メッセージを、通知コードと、コントロール id の連続する範囲に基づいてハンドラー関数にマップします。|

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

オブジェクトが`CMyExtWindow` WM_PAINT メッセージを受信すると、メッセージは実際の`CMyExtWindow::OnPaint`処理のためにに送られます。 メッセージ`OnPaint`にさらに処理が必要であることが示された場合、メッセージはの`CMyBaseWindow`既定のメッセージマップに送られます。

既定のメッセージマップに加えて、 [ALT_MSG_MAP](#alt_msg_map)を使用して代替メッセージマップを定義することもできます。 常に BEGIN_MSG_MAP を使用してメッセージマップを開始します。 その後、後続の代替メッセージマップを宣言できます。 次の例は、既定のメッセージマップと1つの代替メッセージマップを示しています。それぞれに1つのハンドラー関数が含まれています。

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

次の例では、2つの代替メッセージマップを示します。 既定のメッセージマップが空です。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 BEGIN_MSG_MAP と END_MSG_MAP のインスタンスは常に1つだけであることに注意してください。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

メッセージマップのエントリを定義します。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>パラメーター

*Th"クラス"*<br/>
からメッセージマップを格納している基本クラスの名前。

*msgMapID*<br/>
からメッセージマップの識別子。

### <a name="remarks"></a>Remarks

CHAIN_MSG_MAP_ALT は、メッセージを基底クラスの代替メッセージマップに送信します。 この代替メッセージマップを[ALT_MSG_MAP (msgMapID)](#alt_msg_map)と宣言しておく必要があります。 [BEGIN_MSG_MAP](#begin_msg_map)で宣言された基底クラスの既定のメッセージマップにメッセージを転送するには、CHAIN_MSG_MAP を使用します。 例については、「 [CHAIN_MSG_MAP](#chain_msg_map)」を参照してください。

> [!NOTE]
>  常に BEGIN_MSG_MAP を使用してメッセージマップを開始します。 その後、ALT_MSG_MAP を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

メッセージマップのエントリを定義します。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>パラメーター

*Thのメンバー*<br/>
からメッセージマップを格納しているデータメンバーの名前。

*msgMapID*<br/>
からメッセージマップの識別子。

### <a name="remarks"></a>Remarks

CHAIN_MSG_MAP_ALT_MEMBER は、メッセージをデータメンバー内の代替メッセージマップに送信します。 この代替メッセージマップを[ALT_MSG_MAP (msgMapID)](#alt_msg_map)と宣言しておく必要があります。 [BEGIN_MSG_MAP](#begin_msg_map)で宣言されたデータメンバーの既定のメッセージマップにメッセージを転送するには、CHAIN_MSG_MAP_MEMBER を使用します。 例については、「 [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)」を参照してください。

> [!NOTE]
>  常に BEGIN_MSG_MAP を使用してメッセージマップを開始します。 その後、ALT_MSG_MAP を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP

メッセージマップのエントリを定義します。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>パラメーター

*Th"クラス"*<br/>
からメッセージマップを格納している基本クラスの名前。

### <a name="remarks"></a>Remarks

CHAIN_MSG_MAP は、メッセージを基底クラスの既定のメッセージマップ ( [BEGIN_MSG_MAP](#begin_msg_map)で宣言) に送信します。 [ALT_MSG_MAP](#alt_msg_map)で宣言された基底クラスの代替メッセージマップにメッセージを送信するには、 [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)を使用します。

> [!NOTE]
>  常に BEGIN_MSG_MAP を使用してメッセージマップを開始します。 その後、ALT_MSG_MAP を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

次に例を示します。

- ウィンドウプロシージャが既定のメッセージ`CMyClass` `OnPaint`マップを使用していて、メッセージを処理しない場合、メッセージ`CMyBaseClass`は、処理のために既定のメッセージマップに送られます。

- ウィンドウプロシージャがの`CMyClass`最初の代替メッセージマップを使用している場合は、すべてのメッセージが既定のメッセージマップに`CMyBaseClass`送られます。

- ウィンドウプロシージャが2番目`CMyClass`の代替メッセージ`OnChar`マップを使用していて、メッセージを処理しない場合、メッセージはの`CMyBaseClass`指定した代替メッセージマップに送られます。 `CMyBaseClass`では、このメッセージマップを ALT_MSG_MAP (1) として宣言する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

メッセージマップのエントリを定義します。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>パラメーター

*dynaChainID*<br/>
からオブジェクトのメッセージマップの一意の識別子。

### <a name="remarks"></a>Remarks

CHAIN_MSG_MAP_DYNAMIC は、メッセージを実行時に別のオブジェクトの既定のメッセージマップに送信します。 オブジェクトとそのメッセージマップは、 [CDynamicChain:: SetChainEntry](cdynamicchain-class.md#setchainentry)を使用して定義する*dynaChainID*に関連付けられています。 CHAIN_MSG_MAP_DYNAMIC を使用するには`CDynamicChain` 、からクラスを派生させる必要があります。 例については、「 [CDynamicChain](../../atl/reference/cdynamicchain-class.md)の概要」を参照してください。

> [!NOTE]
>  常に[BEGIN_MSG_MAP](#begin_msg_map)を使用してメッセージマップを開始します。 その後、ALT_MSG_MAP を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

メッセージマップのエントリを定義します。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>パラメーター

*Thのメンバー*<br/>
からメッセージマップを格納しているデータメンバーの名前。

### <a name="remarks"></a>Remarks

CHAIN_MSG_MAP_MEMBER は、 [BEGIN_MSG_MAP](#begin_msg_map)で宣言されたデータメンバーの既定のメッセージマップにメッセージを送信します。 [ALT_MSG_MAP](#alt_msg_map)で宣言されたデータメンバーの代替メッセージマップにメッセージを送信するには、 [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)を使用します。

> [!NOTE]
>  常に BEGIN_MSG_MAP を使用してメッセージマップを開始します。 その後、ALT_MSG_MAP を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

次に例を示します。

- ウィンドウプロシージャが既定のメッセージ`CMyClass` `OnPaint`マップを使用していて、メッセージを処理しない場合、メッセージ`m_obj`は、処理のために既定のメッセージマップに送られます。

- ウィンドウプロシージャがの`CMyClass`最初の代替メッセージマップを使用している場合は、すべてのメッセージが既定のメッセージマップに`m_obj`送られます。

- ウィンドウプロシージャが2番目`CMyClass`の代替メッセージマップを使用`OnChar`していて、メッセージを処理しない場合、メッセージはの`m_obj`指定した代替メッセージマップに送られます。 クラス`CMyContainedClass`では、このメッセージマップを ALT_MSG_MAP (1) として宣言する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

[COMMAND_HANDLER](#command_handler)と同様ですが、通知コードにのみ基づいて[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージをマップします。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>パラメーター

*code*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="command_handler"></a>  COMMAND_HANDLER

メッセージマップのエントリを定義します。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメニュー項目、コントロール、またはアクセラレータの識別子。

*code*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

COMMAND_HANDLER は、通知コードとコントロール id に基づいて、指定されたハンドラー関数に[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージをマップします。 例:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

COMMAND_HANDLER マクロで指定する関数は、次のように定義する必要があります。

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

メッセージマップは、 `bHandled`が呼び出される`CommandHandler`前に TRUE に設定されます。 が`CommandHandler`メッセージを完全に処理しない場合は、 `bHandled`メッセージがさらに処理する必要があることを示すために、を FALSE に設定する必要があります。

> [!NOTE]
>  常に[BEGIN_MSG_MAP](#begin_msg_map)を使用してメッセージマップを開始します。 その後、 [ALT_MSG_MAP](#alt_msg_map)を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

COMMAND_HANDLER に加えて、 [MESSAGE_HANDLER](#message_handler)を使用して、識別子やコードに関係なく、WM_COMMAND メッセージをマップすることもできます。 この場合、 `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`はすべての WM_COMMAND メッセージをに`OnHandlerFunction`送信します。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

[COMMAND_HANDLER](#command_handler)に似ていますが、は、メニュー項目、コントロール、またはアクセラレータの識別子にのみ基づいて[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージをマップします。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメッセージを送信するメニュー項目、コントロール、またはアクセラレータの識別子。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

[COMMAND_RANGE_HANDLER](#command_range_handler)に似ていますが、特定の通知コードを持つ[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを、特定の種類のコントロールから1つのハンドラー関数にマップします。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*code*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

この範囲は、メッセージを送信するメニュー項目、コントロール、またはアクセラレータの識別子に基づいています。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

[COMMAND_HANDLER](#command_handler)と同様ですが、1つの範囲のコントロールからの[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを1つのハンドラー関数にマップします。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

この範囲は、メッセージを送信するメニュー項目、コントロール、またはアクセラレータの識別子に基づいています。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

空のメッセージマップを宣言します。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Remarks

DECLARE_EMPTY_MSG_MAP は、マクロ[BEGIN_MSG_MAP](#begin_msg_map)と[END_MSG_MAP](#end_msg_map)を呼び出して空のメッセージマップを作成するための便利なマクロです。

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

リフレクションされたメッセージを受信する子ウィンドウ (コントロール) の既定のハンドラーを提供します。ハンドラーは、ハンドルされてい`DefWindowProc`ないメッセージをに適切に渡します。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="end_msg_map"></a>END_MSG_MAP

メッセージマップの終了をマークします。

```
END_MSG_MAP()
```

### <a name="remarks"></a>Remarks

メッセージマップの先頭をマークするには、常に[BEGIN_MSG_MAP](#begin_msg_map)マクロを使用します。 [ALT_MSG_MAP](#alt_msg_map)を使用して、後続の代替メッセージマップを宣言します。

BEGIN_MSG_MAP と END_MSG_MAP のインスタンスは常に1つだけであることに注意してください。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="example"></a>例

次の例は、既定のメッセージマップと1つの代替メッセージマップを示しています。それぞれに1つのハンドラー関数が含まれています。

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

次の例では、2つの代替メッセージマップを示します。 既定のメッセージマップが空です。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

通知メッセージを親ウィンドウに転送します。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Remarks

このマクロをメッセージマップの一部として指定します。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

メッセージマップのエントリを定義します。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>パラメーター

*msg*<br/>
からWindows メッセージ。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

MESSAGE_HANDLER は、Windows メッセージを指定されたハンドラー関数にマップします。

MESSAGE_HANDLER マクロで指定する関数は、次のように定義する必要があります。

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

メッセージマップは、 `bHandled`が呼び出される`MessageHandler`前に TRUE に設定されます。 が`MessageHandler`メッセージを完全に処理しない場合は、 `bHandled`メッセージがさらに処理する必要があることを示すために、を FALSE に設定する必要があります。

> [!NOTE]
>  常に[BEGIN_MSG_MAP](#begin_msg_map)を使用してメッセージマップを開始します。 その後、 [ALT_MSG_MAP](#alt_msg_map)を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

MESSAGE_HANDLER に加えて、 [COMMAND_HANDLER](#command_handler)と[NOTIFY_HANDLER](#notify_handler)を使用して、 [WM_COMMAND](/windows/win32/menurc/wm-command)メッセージと[WM_NOTIFY](/windows/win32/controls/wm-notify)メッセージをそれぞれマップすることができます。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

[MESSAGE_HANDLER](#message_handler)に似ていますが、Windows メッセージの範囲を1つのハンドラー関数にマップします。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>パラメーター

*msgFirst*<br/>
から連続したメッセージの範囲の先頭をマークします。

*msgLast*<br/>
からメッセージの連続する範囲の末尾をマークします。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

[NOTIFY_HANDLER](#notify_handler)と同様ですが、通知コードのみに基づいて[WM_NOTIFY](/windows/win32/controls/wm-notify)メッセージをマップします。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>パラメーター

*定期*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="notify_handler"></a>NOTIFY_HANDLER

メッセージマップのエントリを定義します。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメッセージを送信するコントロールの識別子。

*定期*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

NOTIFY_HANDLER は、通知コードおよびコントロール識別子に基づいて、指定されたハンドラー関数に[WM_NOTIFY](/windows/win32/controls/wm-notify)メッセージをマップします。

NOTIFY_HANDLER マクロで指定する関数は、次のように定義する必要があります。

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

メッセージマップは、 `bHandled`が呼び出される`NotifyHandler`前に TRUE に設定されます。 が`NotifyHandler`メッセージを完全に処理しない場合は、 `bHandled`メッセージがさらに処理する必要があることを示すために、を FALSE に設定する必要があります。

> [!NOTE]
>  常に[BEGIN_MSG_MAP](#begin_msg_map)を使用してメッセージマップを開始します。 その後、 [ALT_MSG_MAP](#alt_msg_map)を使用して後続の代替メッセージマップを宣言できます。 [END_MSG_MAP](#end_msg_map)マクロは、メッセージマップの末尾をマークします。 すべてのメッセージマップには、BEGIN_MSG_MAP と END_MSG_MAP のインスタンスを1つだけ指定する必要があります。

NOTIFY_HANDLER に加えて、 [MESSAGE_HANDLER](#message_handler)を使用して、識別子やコードに関係なく、WM_NOTIFY メッセージをマップすることもできます。 この場合、 `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`はすべての WM_NOTIFY メッセージをに`OnHandlerFunction`送信します。

ATL でのメッセージマップの使用の詳細については、「[メッセージマップ](../../atl/message-maps-atl.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

[NOTIFY_HANDLER](#notify_handler)に似ていますが、コントロール識別子にのみ基づいて[WM_NOTIFY](/windows/win32/controls/wm-notify)メッセージをマップします。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメッセージを送信するコントロールの識別子。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

[NOTIFY_RANGE_HANDLER](#notify_range_handler)に似ていますが、特定の通知コードを持つ[WM_NOTIFY](/windows/win32/controls/wm-notify)メッセージを、特定の種類のコントロールから1つのハンドラー関数にマップします。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*定期*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

この範囲は、メッセージを送信するコントロールの識別子に基づいています。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

[NOTIFY_HANDLER](#notify_handler)と同様ですが、コントロールの範囲から1つのハンドラー関数に[WM_NOTIFY](/windows/win32/controls/wm-notify)メッセージをマップします。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

この範囲は、メッセージを送信するコントロールの識別子に基づいています。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

通知メッセージを送信した子ウィンドウ (コントロール) に返信メッセージを反映します。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Remarks

親ウィンドウのメッセージマップの一部として、このマクロを指定します。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

[COMMAND_CODE_HANDLER](#command_code_handler)に似ていますが、親ウィンドウから反映されたコマンドをマップします。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>パラメーター

*code*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

[COMMAND_HANDLER](#command_handler)に似ていますが、親ウィンドウから反映されたコマンドをマップします。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメニュー項目、コントロール、またはアクセラレータの識別子。

*code*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

[COMMAND_ID_HANDLER](#command_id_handler)に似ていますが、親ウィンドウから反映されたコマンドをマップします。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメニュー項目、コントロール、またはアクセラレータの識別子。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)に似ていますが、親ウィンドウから反映されたコマンドをマップします。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*code*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

[COMMAND_RANGE_HANDLER](#command_range_handler)に似ていますが、親ウィンドウから反映されたコマンドをマップします。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

[NOTIFY_CODE_HANDLER](#notify_code_handler)に似ていますが、親ウィンドウから反映された通知をマップします。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>パラメーター

*定期*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

[NOTIFY_HANDLER](#notify_handler)に似ていますが、親ウィンドウから反映された通知をマップします。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメニュー項目、コントロール、またはアクセラレータの識別子。

*定期*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

[NOTIFY_ID_HANDLER](#notify_id_handler)に似ていますが、親ウィンドウから反映された通知をマップします。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>パラメーター

*id*<br/>
からメニュー項目、コントロール、またはアクセラレータの識別子。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)に似ていますが、親ウィンドウから反映された通知をマップします。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*定期*<br/>
から通知コード。

*func*<br/>
からメッセージハンドラー関数の名前。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

[NOTIFY_RANGE_HANDLER](#notify_range_handler)に似ていますが、親ウィンドウから反映された通知をマップします。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>パラメーター

*idFirst*<br/>
からコントロール id の連続する範囲の開始をマークします。

*idLast*<br/>
からコントロール id の連続する範囲の末尾をマークします。

*func*<br/>
からメッセージハンドラー関数の名前。

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
