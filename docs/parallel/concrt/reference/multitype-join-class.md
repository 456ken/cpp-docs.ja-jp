---
title: multitype_join クラス
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 7a0c68c2c017eedfa23548bee1d17177e8eaaa1e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289027"
---
# <a name="multitypejoin-class"></a>multitype_join クラス

`multitype_join` メッセージング ブロックは、複数のソースと単一のターゲットを持つメッセージング ブロックで、それぞれのソースから受け取った異なる種類のメッセージを 1 つに結合して、結合されたメッセージのタプルをターゲットに渡します。

## <a name="syntax"></a>構文

```
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
`tuple`メッセージのペイロードの種類が参加しているし、ブロックによって反映されます。

*_Jtype*<br/>
種類の`join`ブロックか、これは`greedy`または `non_greedy`

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`type`|型の別名の`T`します。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[multitype_join](#ctor)|オーバーロードされます。 `multitype_join` メッセージング ブロックを構築します。|
|[~ multitype_join デストラクター](#dtor)|破棄、`multitype_join`メッセージング ブロックします。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[accept](#accept)|これによって提供されたメッセージを受け入れる`multitype_join`ブロック、呼び出し元に所有権を転送します。|
|[acquire_ref](#acquire_ref)|この参照カウントを取得`multitype_join`メッセージング ブロックは、削除されないようにします。|
|[使用します。](#consume)|によって以前に提供されたメッセージを使用して、`multitype_join`メッセージング ブロックと、呼び出し元に所有権を譲渡する、ターゲットが正常に予約されています。|
|[link_target](#link_target)|このターゲット ブロックにリンク`multitype_join`メッセージング ブロックします。|
|[release](#release)|以前に成功したメッセージの予約を解放します。|
|[release_ref](#release_ref)|この参照カウントを解放`multiple_join`メッセージング ブロックします。|
|[reserve](#reserve)|これによって以前に提供されたメッセージを予約`multitype_join`メッセージング ブロックします。|
|[unlink_target](#unlink_target)|これからのターゲット ブロックを解除`multitype_join`メッセージング ブロックします。|
|[unlink_targets](#unlink_targets)|これからのすべてのターゲットのリンクを解除`multitype_join`メッセージング ブロックします。 (上書き[isource::unlink_targets](isource-class.md#unlink_targets))。|

## <a name="remarks"></a>Remarks

詳細については、次を参照してください。[非同期メッセージ ブロック](../../../parallel/concrt/asynchronous-message-blocks.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>必要条件

**ヘッダー:** agents.h

**名前空間:** concurrency

##  <a name="accept"></a> そのまま使用します。

これによって提供されたメッセージを受け入れる`multitype_join`ブロック、呼び出し元に所有権を転送します。

```
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
`runtime_object_identity` 、提供されたの`message`オブジェクト。

*_PTarget*<br/>
呼び出すターゲット ブロックへのポインター、`accept`メソッド。

### <a name="return-value"></a>戻り値

呼び出し元が現在の所有権を持つメッセージへのポインター。

##  <a name="acquire_ref"></a> acquire_ref

この参照カウントを取得`multitype_join`メッセージング ブロックは、削除されないようにします。

```
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出してターゲット ブロックへのポインター。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、`ITarget`中にこのソースにリンクされているオブジェクト、`link_target`メソッド。

##  <a name="consume"></a> 使用します。

によって以前に提供されたメッセージを使用して、`multitype_join`メッセージング ブロックと、呼び出し元に所有権を譲渡する、ターゲットが正常に予約されています。

```
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
`runtime_object_identity` 、予約済みの`message`オブジェクト。

*_PTarget*<br/>
呼び出すターゲット ブロックへのポインター、`consume`メソッド。

### <a name="return-value"></a>戻り値

ポインター、`message`呼び出し元は、の所有権を今すぐにオブジェクトします。

### <a name="remarks"></a>Remarks

`consume`メソッドは`accept`への呼び出しでは前に必ず必要がありますが、`reserve`返さ**true**します。

##  <a name="link_target"></a> link_target

このターゲット ブロックにリンク`multitype_join`メッセージング ブロックします。

```
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
ポインター、`ITarget`ブロックにリンクするこの`multitype_join`メッセージング ブロックします。

##  <a name="ctor"></a> multitype_join

`multitype_join` メッセージング ブロックを構築します。

```
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>パラメーター

*_Tuple*<br/>
この `tuple` メッセージング ブロックのソースの `multitype_join` です。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

*_Join*<br/>
コピー元の `multitype_join` メッセージング ブロックです。 元のオブジェクトが孤立しており、これが移動コンストラクターになることに注意してください。

### <a name="remarks"></a>Remarks

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

移動の構築はロックの状況では行われません。ということは、移動時に処理中の軽量タスクがないことを確認するのはユーザーの責任です。 そうしないと、例外または不整合な状態で、多数の競合が発生します。

##  <a name="dtor"></a> ~multitype_join

破棄、`multitype_join`メッセージング ブロックします。

```
~multitype_join();
```

##  <a name="release"></a> リリース

以前に成功したメッセージの予約を解放します。

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
`runtime_object_identity`の`message`リリースされているオブジェクトします。

*_PTarget*<br/>
呼び出すターゲット ブロックへのポインター、`release`メソッド。

##  <a name="release_ref"></a> release_ref

この参照カウントを解放`multiple_join`メッセージング ブロックします。

```
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出してターゲット ブロックへのポインター。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、`ITarget`このソースからリンクが解除されるオブジェクト。 ソース ブロックは、ターゲット ブロック用に予約されたリソースを解放できます。

##  <a name="reserve"></a> 予約

これによって以前に提供されたメッセージを予約`multitype_join`メッセージング ブロックします。

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
`runtime_object_identity`の`message`予約されているオブジェクトします。

*_PTarget*<br/>
呼び出すターゲット ブロックへのポインター、`reserve`メソッド。

### <a name="return-value"></a>戻り値

`true` 場合は、メッセージが正常に予約された、`false`それ以外の場合。 予約はなど、多くの理由で失敗します。 メッセージが既に予約またはソースでした、予約を拒否する、など別のターゲットによって受け入れします。

### <a name="remarks"></a>Remarks

呼び出した後`reserve`、成功した場合、いずれかを呼び出す必要があります`consume`または`release`または所有している、メッセージをそれぞれ付与するためにします。

##  <a name="unlink_target"></a> unlink_target

これからのターゲット ブロックを解除`multitype_join`メッセージング ブロックします。

```
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
ポインター、`ITarget`これからのリンクを解除するブロック`multitype_join`メッセージング ブロックします。

##  <a name="unlink_targets"></a> unlink_targets

これからのすべてのターゲットのリンクを解除`multitype_join`メッセージング ブロックします。

```
virtual void unlink_targets();
```

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[choice クラス](choice-class.md)<br/>
[join クラス](join-class.md)
