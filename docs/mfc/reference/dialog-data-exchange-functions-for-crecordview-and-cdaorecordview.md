---
title: CRecordView と CDaoRecordView のダイアログ データ エクスチェンジ (DDX) 関数
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 078e0f450514881084786086683ac026e15ea8be
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095776"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView と CDaoRecordView のダイアログ データ エクスチェンジ (DDX) 関数

このトピックでは、 [CRecordset](../../mfc/reference/crecordset-class.md)と[CRecordView](../../mfc/reference/crecordview-class.md)フォームまたは[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)と[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)の間でデータを交換するために使用される DDX_Field 関数の一覧を示します。 DAO は Access データベースで使用され、Office 2013 でサポートされています。 3.6 は最終バージョンであり、廃止されたと見なされます。

> [!NOTE]
>  DDX_Field 関数は、フォーム内のコントロールとデータを交換するという形で、DDX 関数に似ています。 ただし、DDX とは異なり、レコードビュー自体のフィールドではなく、ビューの関連するレコードセットオブジェクトのフィールドとデータを交換します。 詳細については、 `CRecordView` 「 `CDaoRecordView`クラス」と「」を参照してください。

### <a name="ddx_field-functions"></a>DDX_Field 関数

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)のコンボボックスで、レコードセットフィールドのデータメンバーと現在選択されている項目のインデックスの間で、整数データを転送します。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|または`CRecordView` `CString` で、レコードセットフィールドのデータメンバーとコンボボックスのエディットコントロールとの間でデータを`CDaoRecordView`転送します。 レコードセットからコントロールにデータを移動すると、この関数は、コンボボックス内の指定した文字列内の文字で始まる項目を選択します。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|または`CRecordView` `CString` で、レコードセットフィールドのデータメンバーとコンボボックスのエディットコントロールとの間でデータを`CDaoRecordView`転送します。 レコードセットからコントロールにデータを移動するとき、この関数は、コンボボックス内の指定した文字列と完全に一致する項目を選択します。|
|[DDX_FieldCheck](#ddx_fieldcheck)|レコードセットフィールドのデータメンバーと`CRecordView`または`CDaoRecordView`のチェックボックスの間でブール型のデータを転送します。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|`CRecordView`または`CDaoRecordView`のリストボックス内で、レコードセットフィールドのデータメンバーと現在選択されている項目のインデックスの間で、整数データを転送します。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|リストボックスコントロールとレコードセットのフィールドデータメンバーとの間での[CString](../../atl-mfc-shared/reference/cstringt-class.md)データの転送を管理します。 レコードセットからコントロールにデータを移動すると、この関数は、リストボックス内の指定した文字列内の文字で始まる項目を選択します。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|リストボックスコントロールと`CString`レコードセットのフィールドデータメンバーとの間のデータ転送を管理します。 レコードセットからコントロールにデータを移動するとき、この関数は、指定した文字列と完全に一致する最初の項目を選択します。|
|[DDX_FieldRadio](#ddx_fieldradio)|`CRecordView`または`CDaoRecordView`で、レコードセットフィールドのデータメンバーとオプションボタンのグループとの間で、整数データを転送します。|
|[DDX_FieldScroll](#ddx_fieldscroll)|`CRecordView` また`CDaoRecordView`はのスクロールバーコントロールのスクロール位置を設定または取得します。 [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)関数からを呼び出します。|
|[DDX_FieldSlider](#ddx_fieldslider)|レコードビュー内のスライダーコントロールのつまみ位置と`int`レコードセットのフィールドデータメンバーを同期します。 |
|[DDX_FieldText](#ddx_fieldtext)|`int`転送、 **UINT**、 **long**、 `DWORD`、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)、 **float**、 **double**、 **short**、 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)、および[COleCurrency](../../mfc/reference/colecurrency-class.md)の各データには、オーバーロードされたバージョンを使用できます。レコードセットフィールドのデータメンバーと、 `CRecordView`または`CDaoRecordView`のエディットボックスの間。|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

関数`DDX_FieldCBIndex`は、レコードビュー内のコンボボックスコントロールのリストボックスコントロール内の選択された項目のインデックス`int`と、レコードビューに関連付けられているレコードセットのフィールドデータメンバーを同期します。

```
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*index*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットからコントロールにデータを移動するとき、この関数は、 *index*で指定された値に基づいてコントロールの選択を設定します。 レコードセットからコントロールへの転送で、レコードセットフィールドが Null の場合、MFC はインデックスの値を0に設定します。 コントロールからレコードセットへの転送で、コントロールが空の場合、または項目が選択されていない場合、レコードセットフィールドは0に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 この例は、に似`DDX_FieldCBIndex`ています。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdao

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

`DDX_FieldCBString` 関数は、レコードビュー内のコンボボックスコントロールの編集コントロールと、レコードビューに関連付けられているレコードセットの `CString` フィールドデータメンバーとの間で、[CString](../../atl-mfc-shared/reference/cstringt-class.md)データの転送を管理します。

```
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットからコントロールにデータを移動するとき、この関数は、コンボボックスの現在の選択範囲を、[*値*] に指定された文字列の文字で始まる最初の行に設定します。 レコードセットからコントロールへの転送では、レコードセットフィールドが Null の場合、コンボボックスから選択が削除され、コンボボックスの編集コントロールが空に設定されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、フィールドがを許可する場合、レコードセットフィールドは Null に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 この例には、の`DDX_FieldCBString`呼び出しが含まれています。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

`DDX_FieldCBStringExact` 関数は、レコードビュー内のコンボボックスコントロールの編集コントロールと、レコードビューに関連付けられているレコードセットの `CString` フィールドデータメンバーとの間で、[CString](../../atl-mfc-shared/reference/cstringt-class.md)データの転送を管理します。

```
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットからコントロールにデータを移動するとき、この関数は、コンボボックスの現在の選択範囲を、[*値*] に指定された文字列と完全に一致する最初の行に設定します。 レコードセットからコントロールへの転送では、レコードセットフィールドが NULL の場合、コンボボックスから選択が削除され、コンボボックスのエディットボックスが空に設定されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドは NULL に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 の`DDX_FieldCBStringExact`呼び出しは似ています。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck

この`DDX_FieldCheck`関数は、ダイアログボックス、フォームビュー、またはコントロールビューオブジェクトのチェックボックスコントロールと、ダイアログボックス、フォームビュー、またはコントロールビューオブジェクトの**int**データメンバー間の**int**データの転送を管理します。

```
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
コントロールプロパティに関連付けられているチェックボックスコントロールのリソース ID。

*value*<br/>
データの交換に使用するダイアログボックス、フォームビュー、またはコントロールビューオブジェクトのメンバー変数への参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

が`DDX_FieldCheck`呼び出されたときに、*値*がチェックボックスコントロールの現在の状態に設定されているか、転送の方向に応じてコントロールの状態が*value*に設定されています。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex

関数`DDX_FieldLBIndex`は、レコードビューのリストボックスコントロール内の選択された項目のインデックスと、レコードビューに関連付けられているレコードセットの**int**フィールドデータメンバーを同期します。

```
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*index*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットからコントロールにデータを移動するとき、この関数は、 *index*で指定された値に基づいてコントロールの選択を設定します。 レコードセットからコントロールへの転送で、レコードセットフィールドが Null の場合、MFC はインデックスの値を0に設定します。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドは0に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString

は`DDX_FieldLBString` 、レコードビューにあるリストボックスコントロールの現在の選択項目を、レコードビューに関連付けられているレコードセットの[CString](../../atl-mfc-shared/reference/cstringt-class.md)フィールドデータメンバーにコピーします。

```
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

逆方向では、この関数は、リストボックスの現在の選択範囲を、*値*で指定された文字列内の文字で始まる最初の行に設定します。 レコードセットからコントロールへの転送では、レコードセットフィールドが Null の場合、リストボックスから任意の選択が削除されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドは Null に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 の`DDX_FieldLBString`呼び出しは似ています。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact

関数`DDX_FieldLBStringExact`は、レコードビューにあるリストボックスコントロールの現在の選択項目を、レコードビューに関連付けられているレコードセットの[CString](../../atl-mfc-shared/reference/cstringt-class.md)フィールドデータメンバーにコピーします。

```
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

逆方向では、この関数は、リストボックスの現在の選択項目を [*値*] に指定された文字列と完全に一致する最初の行に設定します。 レコードセットからコントロールへの転送では、レコードセットフィールドが Null の場合、リストボックスから任意の選択が削除されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドは Null に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 の`DDX_FieldLBStringExact`呼び出しは似ています。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio

関数`DDX_FieldRadio`は、レコードビューのレコードセットの0から始まる**int**メンバー変数を、[レコード] ビューのラジオボタンのグループで現在選択されているオプションボタンと関連付けます。

```
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクトの隣接するラジオボタンコントロールのグループ (スタイル WS_GROUP) の最初のの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットフィールドからビューに転送する場合、この関数は、 *n 番目*のオプションボタン (0 から始まる) をオンにして、他のボタンをオフにします。 逆方向では、この関数はレコードセットフィールドを現在オン (オン) になっているラジオボタンの序数に設定します。 レコードセットからコントロールへの転送で、レコードセットフィールドが Null の場合、[いいえ] ボタンは選択されていません。 コントロールからレコードセットへの転送では、コントロールが選択されていない場合、フィールドで許可されている場合、レコードセットフィールドは Null に設定されます。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 の`DDX_FieldRadio`呼び出しは似ています。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

関数`DDX_FieldScroll`は、レコードビューのスクロールバーコントロールのスクロール位置と、レコードビューに関連付けられたレコードセットの**int**フィールドデータメンバー (または、マップ先として選択した任意の整数変数) を同期します。

```
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクトの隣接するラジオボタンコントロールのグループ (スタイル WS_GROUP) の最初のの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットからコントロールにデータを移動するとき、この関数は、スクロールバーコントロールのスクロール位置を [*値*] に指定された値に設定します。 レコードセットからコントロールへの転送では、レコードセットフィールドが Null の場合、スクロールバーコントロールは0に設定されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドの値は0になります。

ODBC ベースのクラスを操作する場合は、最初のバージョンを使用します。 DAO ベースのクラスを操作する場合は、2番目のバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 の`DDX_FieldScroll`呼び出しは似ています。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

  ## <a name="ddx_fieldslider"></a>DDX_FieldSlider
関数`DDX_FieldSlider`は、レコードビューのスライダーコントロールのつまみ位置と、レコードビューに関連付けられているレコードセットの**int**フィールドデータメンバー (または、マップ先として選択した任意の整数変数) を同期します。

### <a name="syntax"></a>構文

  ```
   void AFXAPI DDX_FieldSlider(
       CDataExchange* pDX,
       int nIDC,
       int& value,
       CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
スライダーコントロールのリソース ID。

*value*<br/>
交換する値への参照。 このパラメーターは、スライダーコントロールの現在のつまみの位置を設定するために使用されます。

*pRecordset*<br/>
データの交換に使用`CRecordset`する`CDaoRecordset` 、関連付けられたオブジェクトまたはオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

レコードセットからスライダーにデータを移動すると、この関数はスライダーの位置を [*値*] に指定された値に設定します。 レコードセットからコントロールへの転送で、レコードセットフィールドが Null の場合、スライダーコントロールの位置は0に設定されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドの値は0になります。

`DDX_FieldSlider`は、単なる位置ではなく範囲を設定できるスライダーコントロールと範囲情報を交換しません。

ODBC ベースのクラスを操作する場合は、関数の最初のオーバーライドを使用します。 DAO ベースのクラスで2番目のオーバーライドを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../dialog-data-exchange-and-validation.md)」を参照してください。 `CRecordView` および`CDaoRecordView`フィールドの DDX の例と詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。 スライダーコントロールの詳細については、「 [Using csliderctrl 使い方](../using-csliderctrl.md)」を参照してください。

### <a name="example"></a>例

一般的な DDX_Field の例については、「 [DDX_FieldText](#ddx_fieldtext) 」を参照してください。 の`DDX_FieldSlider`呼び出しは似ています。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdao

##  <a name="ddx_fieldtext"></a>  DDX_FieldText

関数`DDX_FieldText`は、エディットボックスコントロールとのフィールドデータメンバーの間で、 **int**、 **short**、 **long**、DWORD、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)、 **float**、 **double**、 **BOOL**、または**BYTE**データの転送を管理します。レコードセット.

```
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)または[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)オブジェクト内のコントロールの ID。

*value*<br/>
関連付けられ`CRecordset`たオブジェクトまたは`CDaoRecordset`オブジェクトのフィールドデータメンバーへの参照。 値のデータ型は、使用するの`DDX_FieldText`オーバーロードされたバージョンによって異なります。

*pRecordset*<br/>
データが交換される[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインター。 このポインターは`DDX_FieldText` 、が Null 値を検出して設定できるようにします。

### <a name="remarks"></a>Remarks

[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトの場合`DDX_FieldText` 、は、 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)および[COleCurrency](../../mfc/reference/colecurrency-class.md)値の転送も管理します。 空のエディットボックスコントロールは、Null 値を示します。 レコードセットからコントロールへの転送では、レコードセットフィールドが Null の場合、エディットボックスは空に設定されます。 コントロールからレコードセットへの転送では、コントロールが空の場合、レコードセットフィールドは Null に設定されます。

ODBC ベースのクラスを使用する場合は、 [CRecordset](../../mfc/reference/crecordset-class.md)パラメーターを使用してバージョンを使用します。 DAO ベースのクラスを使用している場合は、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)パラメーターでバージョンを使用します。

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 例と、 [CRecordView](../../mfc/reference/crecordview-class.md)と[CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md)フィールドの DDX の詳細については、「[レコードビュー](../../data/record-views-mfc-data-access.md)」を参照してください。

### <a name="example"></a>例

次の`DoDataExchange`例の[CRecordView](../../mfc/reference/crecordview-class.md)関数に`DDX_FieldText`は、3つのデータ型の関数呼び出しが含まれています。 `IDC_COURSELIST`はコンボボックスで、他の2つのコントロールはエディットボックスです。 DAO プログラミングでは、 *m_pSet*パラメーターは[CRecordset](../../mfc/reference/crecordset-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)へのポインターです。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)
