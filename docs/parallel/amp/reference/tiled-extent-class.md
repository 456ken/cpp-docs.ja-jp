---
title: tiled_extent クラス
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: 51e7696b8103e81d42beec0987a49f26fe041643
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352282"
---
# <a name="tiledextent-class"></a>tiled_extent クラス

`tiled_extent` オブジェクトは 3 つの次元のいずれかの `extent` オブジェクトであり、範囲空間を 1、2、または 3 次元のタイルに再分割します。

### <a name="syntax"></a>構文

```
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
```

### <a name="parameters"></a>パラメーター

*_Dim0*<br/>
最上位の次元の長さ。

*_Dim1*<br/>
最上位の次の次元の長さ。

*_Dim2*<br/>
最下位の次元の長さ。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[tiled_extent コンス トラクター](#ctor)|`tiled_extent` クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|`extent` テンプレート引数 `tiled_extent`、`_Dim0`、および `_Dim1` の値をキャプチャする `_Dim2` オブジェクトを返します。|
|[pad](#pad)|タイルの次元によって均等に分割できる範囲を上方調整した新しい `tiled_extent` オブジェクトを返します。|
|[truncate](#truncate)|タイルの次元によって均等に分割できるように範囲を下方調整した新しい `tiled_extent` オブジェクトを返します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[operator=](#operator_eq)|指定された `tiled_index` オブジェクトの内容をこのオブジェクトにコピーします。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[tile_dim0 定数](#tile_dim0)|最上位の次元の長さを格納します。|
|[tile_dim1 定数](#tile_dim1)|最上位の次の次元の長さを格納します。|
|[tile_dim2 定数](#tile_dim2)|最下位の次元の長さを格納します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[tile_extent](#tile_extent)|`tiled_extent` テンプレート引数 `_Dim0`、`_Dim1`、および `_Dim2` の値をキャプチャする `extent` オブジェクトを取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

`extent`

`tiled_extent`

## <a name="requirements"></a>必要条件

**ヘッダー:** amp.h

**名前空間:** コンカレンシー

## <a name="ctor"> </a>  tiled_extent コンス トラクター

`tiled_extent` クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピーする `extent` オブジェクトまたは `tiled_extent` オブジェクト。

## <a name="get_tile_extent"> </a>  get_tile_extent

返します、`extent`オブジェクトの値をキャプチャする、`tiled_extent`テンプレート引数`_Dim0`、 `_Dim1`、および`_Dim2`します。

### <a name="syntax"></a>構文

```
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>戻り値

この `extent` インスタンスの次元をキャプチャする `tiled_extent` オブジェクト。

## <a name="pad"> </a>  パッド

タイルの次元によって均等に分割できる範囲を上方調整した新しい `tiled_extent` オブジェクトを返します。

### <a name="syntax"></a>構文

```
tiled_extent pad() const;
```

### <a name="return-value"></a>戻り値

新しい `tiled_extent` オブジェクト、値渡し。
## <a name="truncate"> </a>  truncate

タイルの次元によって均等に分割できるように範囲を下方調整した新しい `tiled_extent` オブジェクトを返します。

### <a name="syntax"></a>構文

```
tiled_extent truncate() const;
```

### <a name="return-value"></a>戻り値

タイルの次元によって均等に分割できるように範囲を下方調整した新しい `tiled_extent` オブジェクトを返します。

## <a name="operator_eq"> </a>  operator=

指定された `tiled_index` オブジェクトの内容をこのオブジェクトにコピーします。

### <a name="syntax"></a>構文

```
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元の `tiled_index` オブジェクト。

### <a name="return-value"></a>戻り値

この `tiled_index` インスタンスへの参照。

## <a name="tile_dim0"> </a>  tile_dim0

最上位の次元の長さを格納します。

### <a name="syntax"></a>構文

```
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"> </a>  tile_dim1

最上位の次の次元の長さを格納します。

### <a name="syntax"></a>構文

```
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"> </a>  tile_dim2

最下位の次元の長さを格納します。

### <a name="syntax"></a>構文

```
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"> </a>  tile_extent
  取得、`extent`オブジェクトの値をキャプチャする、`tiled_extent`テンプレート引数`_Dim0`、 `_Dim1`、および`_Dim2`します。

### <a name="syntax"></a>構文

```
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
