---
title: カテゴリに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 9c74b1e8e9fc101ed9b3acd842d38dcdb9eb48f3
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818493"
---
# <a name="category-macros"></a>カテゴリに関するマクロ

これらのマクロは、カテゴリのマップを定義します。

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|カテゴリのマップの先頭をマークします。|
|[END_CATEGORY_MAP](#end_category_map)|カテゴリのマップの最後をマークします。|
|[IMPLEMENTED_CATEGORY](#implemented_category)|COM オブジェクトによって実装されているカテゴリを示します。|
|[REQUIRED_CATEGORY](#required_category)|COM オブジェクトによって、コンテナーに必要なカテゴリを示します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

カテゴリのマップの先頭をマークします。

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
[in]カテゴリのマップを含むクラスの名前。

### <a name="remarks"></a>Remarks

カテゴリのマップを使用して、どの COM クラスが実装で、コンテナーから必要とするカテゴリは、コンポーネントのカテゴリを指定します。

追加、 [IMPLEMENTED_CATEGORY](#implemented_category) COM クラスで実装される各カテゴリ用にマップするエントリ。 追加、[要求する](#required_category)クラスを実装するには、そのクライアントを必要とするカテゴリごとにマップするエントリ。 Map の末尾を示す、 [END_CATEGORY_MAP](#end_category_map)マクロ。

クラスに関連付けられている場合、モジュールが登録されると、マップに示されているコンポーネントのカテゴリを自動的に登録されます[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)または[役立つ](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).

> [!NOTE]
>  ATL では、標準コンポーネント カテゴリ マネージャーを使用して、コンポーネントのカテゴリを登録します。 モジュールが登録されると、マネージャーがシステムに存在しない場合は、登録が成功するしますが、コンポーネントのカテゴリは、そのクラスは登録されません。

コンポーネントのカテゴリの詳細については、次を参照してください。[コンポーネントのカテゴリの概要とどのように動作する](/windows/desktop/com/component-categories-and-how-they-work)Windows SDK に含まれています。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

カテゴリのマップの最後をマークします。

```
END_CATEGORY_MAP()
```

### <a name="example"></a>例

例をご覧ください[BEGIN_CATEGORY_MAP](#begin_category_map)します。

##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY

コンポーネントを IMPLEMENTED_CATEGORY マクロを追加[カテゴリ マップ](#begin_category_map)で識別されるカテゴリを実装するものとして登録するかを指定する、 *catID*パラメーター。

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>パラメーター

*catID*<br/>
[in]CATID 定数または実装されているカテゴリのグローバル一意識別子 (GUID) を保持する変数。 アドレス*catID*取得され、マップに追加されます。 ストック カテゴリの選択は、以下の表を参照してください。

### <a name="remarks"></a>Remarks

クラスに関連付けられている場合、モジュールが登録されると、マップに示されているコンポーネントのカテゴリを自動的に登録されます[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)または[役立つ](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)マクロ。

クライアントは、そのインスタンスを作成するのにことがなくその機能と要件を決定するのにクラスの登録されているカテゴリの情報を使用できます。

コンポーネントのカテゴリの詳細については、次を参照してください。[コンポーネントのカテゴリの概要とどのように動作する](/windows/desktop/com/component-categories-and-how-they-work)Windows SDK に含まれています。

### <a name="a-selection-of-stock-categories"></a>ストック カテゴリの選択

|説明|シンボル|レジストリ GUID|
|-----------------|------------|-------------------|
|安全なスクリプト|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|安全な初期化|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|シンプルなフレーム サイト コンテインメント|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|単純データ バインディング|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|高度なデータ バインディング|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|ウィンドウなしのコントロール|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|インターネットに対応したオブジェクト|参照してください[インターネット対応オブジェクト](/windows/desktop/com/internet-aware-objects)サンプルの一覧については、Windows SDK に含まれています。||

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>  REQUIRED_CATEGORY

要求するマクロをコンポーネントの追加[カテゴリ マップ](#begin_category_map)で識別されるカテゴリを要求するよう登録するかを指定する、 *catID*パラメーター。

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>パラメーター

*catID*<br/>
[in]CATID 定数または必要なカテゴリのグローバル一意識別子 (GUID) を保持する変数。 アドレス*catID*取得され、マップに追加されます。 ストック カテゴリの選択は、以下の表を参照してください。

### <a name="remarks"></a>Remarks

クラスに関連付けられている場合、モジュールが登録されると、マップに示されているコンポーネントのカテゴリを自動的に登録されます[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)または[役立つ](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)マクロ。

クライアントは、そのインスタンスを作成するのにことがなくその機能と要件を決定するのにクラスの登録されているカテゴリの情報を使用できます。 たとえば、コントロールは、コンテナーがデータ バインディングをサポートする必要があります。 コンテナーは、そのコントロールに必要なカテゴリをカテゴリ マネージャーをクエリすることによって、コントロールをホストするために必要な機能があるかどうかを確認できます。 コンテナーが必要な機能をサポートしていない場合、COM オブジェクトをホストする拒否することができます。

サンプルの一覧を含め、コンポーネントのカテゴリの詳細については、次を参照してください。[コンポーネントのカテゴリの概要とどのように動作する](/windows/desktop/com/component-categories-and-how-they-work)Windows SDK に含まれています。

### <a name="a-selection-of-stock-categories"></a>ストック カテゴリの選択

|説明|シンボル|レジストリ GUID|
|-----------------|------------|-------------------|
|安全なスクリプト|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|安全な初期化|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|シンプルなフレーム サイト コンテインメント|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|単純データ バインディング|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|高度なデータ バインディング|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|ウィンドウなしのコントロール|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|インターネットに対応したオブジェクト|参照してください[インターネット対応オブジェクト](/windows/desktop/com/internet-aware-objects)サンプルの一覧については、Windows SDK に含まれています。||

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
