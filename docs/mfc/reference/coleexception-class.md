---
title: COleException クラス
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 4b5dd2de2924b62dd76d7f16a494566849357de8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300363"
---
# <a name="coleexception-class"></a>COleException クラス

OLE 操作に関する例外条件を表します。

## <a name="syntax"></a>構文

```
class COleException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleException::Process](#process)|OLE のリターン コードにキャッチされた例外に変換します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|例外の原因を示すステータス コードが含まれています。|

## <a name="remarks"></a>Remarks

`COleException`クラスには、例外の理由を示すステータス コードを保持するパブリック データ メンバーが含まれています。

一般に、作成しないようにする、`COleException`オブジェクトは、直接呼び出す必要があります[AfxThrowOleException](exception-processing.md#afxthrowoleexception)します。

例外の詳細については、記事をご覧ください。[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)と[例外。OLE の例外](../../mfc/exceptions-ole-exceptions.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

OLE の例外の理由を示すステータス コードを保持します。

```
SCODE m_sc;
```

### <a name="remarks"></a>Remarks

この変数の値によって設定されます[AfxThrowOleException](exception-processing.md#afxthrowoleexception)します。

SCODE の詳細については、次を参照してください。 [COM エラー コードの構造](/windows/desktop/com/structure-of-com-error-codes)Windows SDK に含まれています。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

呼び出す、**プロセス**OLE のステータス コードにキャッチされた例外に変換します。

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>パラメーター

*pAnyException*<br/>
キャッチされた例外へのポインター。

### <a name="return-value"></a>戻り値

OLE のステータス コード。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  この関数は**静的**します。

SCODE の詳細については、次を参照してください。 [COM エラー コードの構造](/windows/desktop/com/structure-of-com-error-codes)Windows SDK に含まれています。

### <a name="example"></a>例

  [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)の例を参照してください。

## <a name="see-also"></a>関連項目

[MFC サンプル CALCDRIV](../../visual-cpp-samples.md)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
