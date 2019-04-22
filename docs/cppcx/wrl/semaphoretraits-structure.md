---
title: SemaphoreTraits 構造体
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: e7bd2e5d0993c8e4be7223d98ffb1dbec14cbb74
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58785579"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits 構造体

一般的な特性を定義、`Semaphore`オブジェクト。

## <a name="syntax"></a>構文

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

名前                               | 説明
---------------------------------- | --------------------------------------
[Semaphoretraits::unlock](#unlock) | 共有リソースのコントロールをリリースします。

## <a name="inheritance-hierarchy"></a>継承階層

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Semaphoretraits::unlock

共有リソースのコントロールをリリースします。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドルを`Semaphore`オブジェクト。

### <a name="remarks"></a>Remarks

場合は、ロック解除操作が成功すると、`Unlock()`エラーの原因を示すエラーを出力します。
