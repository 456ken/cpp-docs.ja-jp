---
title: freelist クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: ef1f2e617e93869a1084dc030c6496c819f1ed96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159393"
---
# <a name="freelist-class"></a>freelist クラス

メモリ ブロックのリストを管理します。

## <a name="syntax"></a>構文

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*sz*|割り当てられる配列内の要素の数。|
|*Max*|フリー リストに格納される要素の最大数を示す最大クラス。 最大クラスは、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_variable_size](../standard-library/max-variable-size-class.md) のいずれかにすることができます。|

## <a name="remarks"></a>Remarks

このテンプレート クラスのサイズのメモリ ブロックのリストを管理する*Sz*で渡される最大クラスによって決定リストの最大長を持つ*最大*します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[freelist](#freelist)|`freelist` 型のオブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[pop](#pop)|フリー リストから最初のメモリ ブロックを削除します。|
|[push](#push)|メモリ ブロックをリストに追加します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="freelist"></a>  freelist::freelist

`freelist` 型のオブジェクトを構築します。

```cpp
freelist();
```

### <a name="remarks"></a>Remarks

## <a name="pop"></a>  freelist::pop

フリー リストから最初のメモリ ブロックを削除します。

```cpp
void *pop();
```

### <a name="return-value"></a>戻り値

一覧から削除するメモリ ブロックへのポインターを返します。

### <a name="remarks"></a>Remarks

リストが空の場合、メンバー関数は NULL を返します。 それ以外の場合は、空き一覧から最初のメモリ ブロックを削除します。

## <a name="push"></a>  freelist::push

メモリ ブロックをリストに追加します。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|フリー リストに追加するメモリ ブロックへのポインター。|

### <a name="return-value"></a>戻り値

**true**場合、`full`最大クラスの関数を返します**false**。 それ以外の`push`関数が返される**false**します。

### <a name="remarks"></a>Remarks

場合、`full`最大クラスの関数を返します**false**、このメンバー関数が指すメモリ ブロックを追加します*ptr*リストの先頭にします。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)<br/>
