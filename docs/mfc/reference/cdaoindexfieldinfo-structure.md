---
title: CDaoIndexFieldInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: d03a6f6eadd4cf6ccb5279edf18675605d0b1485
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304276"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 構造体

`CDaoIndexFieldInfo`構造体には、データ アクセス オブジェクト (DAO) に対して定義されているインデックス フィールド オブジェクトに関する情報が含まれています。

## <a name="syntax"></a>構文

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
インデックスのフィールド オブジェクトの一意名します。 詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

*m_bDescending*<br/>
Index オブジェクトによって定義されているインデックスの順序を示します。 降順の場合は TRUE。

## <a name="remarks"></a>Remarks

Index オブジェクトには、多数のフィールド、フィールドにインデックスがテーブル定義 (またはテーブルに基づくレコード セット) を示すことができます。 上記のプライマリへの参照での情報を返す方法を示します、`m_pFieldInfos`のメンバー、 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)オブジェクトを呼び出すことによって取得、`GetIndexInfo`クラスのメンバー関数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)します。

インデックスおよびインデックスのフィールド オブジェクトは、MFC クラスでは表されません。 DAO オブジェクトを基になる MFC オブジェクト クラスの代わりに、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)インデックス コレクションと呼ばれるインデックス オブジェクトのコレクションを含めることができます。 インデックスの各オブジェクトには、さらに、フィールド オブジェクトのコレクションが含まれています。 これらのクラス メンバー関数のインデックスについては、個々 のアイテムへのアクセスを提供するか、それらを一度にすべてにアクセスできます、`CDaoIndexInfo`オブジェクトを呼び出すことによって、`GetIndexInfo`親オブジェクトのメンバー関数。 `CDaoIndexInfo`オブジェクトを持つデータ メンバー、`m_pFieldInfos`の配列を指す`CDaoIndexFieldInfo`オブジェクト。

呼び出す、`GetIndexInfo`でインデックスがコレクションは、親テーブルまたはレコード セット オブジェクトのメンバー関数は、興味のあるインデックス オブジェクトを格納します。 アクセスし、`m_pFieldInfos`のメンバー、 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)オブジェクト。 長さ、`m_pFieldInfos`に配列が格納されている`m_nFields`します。 `CDaoIndexFieldInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoIndexFieldInfo`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
