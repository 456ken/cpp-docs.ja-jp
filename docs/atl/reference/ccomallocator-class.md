---
title: CComAllocator クラス
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 9f1c005262d25b1ff5e900377c229afe1573e6d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259704"
---
# <a name="ccomallocator-class"></a>CComAllocator クラス

このクラスは、COM メモリのルーチンを使用してメモリを管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class CComAllocator
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|メモリの割り当てにこの静的メソッドを呼び出します。|
|[CComAllocator::Free](#free)|割り当てられたメモリを解放するこの静的メソッドを呼び出します。|
|[CComAllocator::Reallocate](#reallocate)|メモリを再割り当てにこの静的メソッドを呼び出します。|

## <a name="remarks"></a>Remarks

このクラスによって使用されます[CComHeapPtr](../../atl/reference/ccomheapptr-class.md) COM メモリ割り当てルーチンを提供します。 対応するクラス、 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)、CRT ルーチンを使用して同じメソッドを提供します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="allocate"></a>  CComAllocator::Allocate

メモリを割り当てる場合は、この静的関数を呼び出します。

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
割り当てるバイト数。

### <a name="return-value"></a>戻り値

メモリが不足している場合、割り当てられた領域に void ポインターを返すか、NULL を返します。

### <a name="remarks"></a>Remarks

メモリを割り当てます。 参照してください[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)の詳細。

##  <a name="free"></a>  CComAllocator::Free

割り当てられたメモリを解放するため、この静的関数を呼び出します。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
割り当てられたメモリへのポインター。

### <a name="remarks"></a>Remarks

割り当てられたメモリを解放します。 参照してください[CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree)の詳細。

##  <a name="reallocate"></a>  CComAllocator::Reallocate

メモリを再割り当てする場合は、この静的関数を呼び出します。

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
割り当てられたメモリへのポインター。

*nBytes*<br/>
再割り当てするバイト数。

### <a name="return-value"></a>戻り値

メモリ不足がある場合、割り当てられた領域に void ポインターを返します

### <a name="remarks"></a>Remarks

割り当てられたメモリの量を変更します。 参照してください[CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)の詳細。

## <a name="see-also"></a>関連項目

[CComHeapPtr クラス](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator クラス](../../atl/reference/ccrtallocator-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
