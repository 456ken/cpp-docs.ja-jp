---
title: tile_barrier クラス
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: 89e6d972fbecb2674e6343bf6d11f9972c25c63d
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975037"
---
# <a name="tilebarrier-class"></a>tile_barrier クラス

`wait` メソッドを使用してスレッド グループ (タイル) で実行されているスレッドの実行を同期します。 ランタイムのみがこのクラスをインスタンス化できます。

### <a name="syntax"></a>構文

```
class tile_barrier;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[tile_barrier コンス トラクター](#ctor)|`tile_barrier` クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[wait](#wait)|タイルのすべてのスレッドの待機が完了するまで、スレッド グループ (タイル) のすべてのスレッドの実行を停止するように指示します。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|すべてのメモリ アクセスが完了し、タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|すべてのグローバル メモリ アクセスが完了し、タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|すべての `tile_static` メモリ アクセスが完了し、タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。|

## <a name="inheritance-hierarchy"></a>継承階層

`tile_barrier`

## <a name="requirements"></a>必要条件

**ヘッダー:** amp.h

**名前空間:** コンカレンシー

## <a name="ctor"></a>  tile_barrier コンス トラクター

既存のものをコピーすることによって、クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピーする `tile_barrier` オブジェクト。

## <a name="wait"></a>待機

タイルのすべてのスレッドの待機が完了するまで実行を停止するには、スレッド グループ (タイル) のすべてのスレッドに指示します。

### <a name="syntax"></a>構文

```
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a> wait_with_all_memory_fence

タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。 これによって、すべてのメモリ アクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

### <a name="syntax"></a>構文

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewaitwithglobalmemoryfence-waitwithglobalmemoryfence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。 これによって、すべてのグローバル メモリ アクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

### <a name="syntax"></a>構文

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewaitwithtilestaticmemoryfence-waitwithtilestaticmemoryfence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。 これにより`tile_static`メモリ アクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

### <a name="syntax"></a>構文

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
