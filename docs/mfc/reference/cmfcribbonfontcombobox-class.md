---
title: CMFCRibbonFontComboBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 643e2a519c6d96c1070990dd86d571c5b7c09f95
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288429"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox クラス

フォントの一覧を含むコンボ ボックスを実装します。 このコンボ ボックスをリボン パネルに配置できます。

## <a name="syntax"></a>構文

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|デストラクターです。|

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|
  `CMFCRibbonFontComboBox` オブジェクトを構築して初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|リボンのフォント コンボ ボックスに、指定されたフォントの種類、文字セット、ピッチ、ファミリのフォントを設定します。|
|`CMFCRibbonFontComboBox::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|指定された文字セットを返します。|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|コンボ ボックスに表示するフォントの種類を返します。 有効なオプションは、DEVICE_FONTTYPE、RASTER_FONTTYPE、TRUETYPE_FONTTYPE、またはそのビットごとの任意の組み合わせです。|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|コンボ ボックスに表示されるフォントのピッチとファミリを返します。|
|`CMFCRibbonFontComboBox::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|リボンのフォント コンボ ボックスに、以前に指定されたフォントの種類、文字セット、ピッチ、ファミリのフォントを設定します。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|コンボ ボックスで、指定されたフォントを選択します。|

## <a name="remarks"></a>Remarks

作成した後、`CMFCRibbonFontComboBox`オブジェクトを呼び出してリボン パネルに追加[cmfcribbonpanel::add](../../mfc/reference/cmfcribbonpanel-class.md#add)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonComboBox.h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

フォントでリボンのコンボ ボックスに表示します。

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>パラメーター

*nFontType*<br/>
[in]追加するフォントのフォントの種類を指定します。

*nCharSet*<br/>
[in]追加するフォントの文字セットを指定します。

*nPitchAndFamily*<br/>
[in]ピッチおよび追加するフォントのファミリを指定します。

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

構築し、初期化、 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)オブジェクト。

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]ユーザーがコンボ ボックスから項目を選択したときに実行されるコマンドのコマンド ID。

*nFontType*<br/>
[in]コンボ ボックスに表示するフォントの種類を指定します。 有効なオプションは、DEVICE_FONTTYPE、RASTER_FONTTYPE、TRUETYPE_FONTTYPE、またはそのビットごとの任意の組み合わせです。

*nCharSet*<br/>
[in]指定された文字セットに属するものをコンボ ボックス内のフォントをフィルター処理.

*nPitchAndFamily*<br/>
[in]ピッチとファミリのコンボ ボックスに表示されるフォントを指定します。

*nWidth*<br/>
[in]コンボ ボックスのピクセル単位の幅を指定します。

### <a name="remarks"></a>Remarks

可能な限りの詳細については*nFontType*パラメーターの値を参照してください[EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) Windows SDK のドキュメント。

割り当てることができる有効な文字セットの詳細については*nCharSet*、および有効な値を割り当てることができる*nPitchAndFamily*を参照してください[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)で、Windows SDK のドキュメントです。

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>パラメーター

[in] *iIndex*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

以前に指定したフォントの種類、文字セット、およびピッチとファミリのフォントでリボンのコンボ ボックスに表示します。

```
void RebuildFonts();
```

### <a name="remarks"></a>Remarks

フォントの種類、文字のセットを指定して、リボンのフォント コンボ ボックスに含めるフォントのピッチとファミリのボックスに、[コンス トラクター](#cmfcribbonfontcombobox)または呼び出すことによって、このクラス[CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

コンボ ボックスで、指定されたフォントを選択します。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>パラメーター

' lpszName * を選択するフォントの名前を指定します。

*nCharSet*<br/>
選択したフォントの文字セットを指定します。

*bExact*<br/>
文字セットは、フォントを選択するときと一致する必要がありますを指定する場合は TRUEフォントを選択するときに、文字セットを無視できることを指定する場合は FALSE。

### <a name="return-value"></a>戻り値

指定したフォントが見つかり、選択されている場合は 0 以外それ以外の場合、0 を返します。

### <a name="remarks"></a>Remarks

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

指定された文字セットを返します。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>戻り値

文字セット (Windows SDK のドキュメントでは、LOGFONT を参照してください)。

### <a name="remarks"></a>Remarks

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

コンボ ボックスに表示するフォントの種類を返します。 有効なオプションは、DEVICE_FONTTYPE、RASTER_FONTTYPE、TRUETYPE_FONTTYPE、またはそのビットごとの任意の組み合わせです。

```
int GetFontType() const;
```

### <a name="return-value"></a>戻り値

フォントの種類 (Windows sdk で EnumFontFamProc を参照してください)。

### <a name="remarks"></a>Remarks

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

コンボ ボックスに表示されるフォントのピッチとファミリを返します。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>戻り値

ピッチとファミリ (Windows SDK のドキュメントでは、LOGFONT を参照してください)。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox クラス](../../mfc/reference/cmfcribboncombobox-class.md)
