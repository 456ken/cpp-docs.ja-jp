---
title: CDaoParameterInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 62addd44f8aa8fceafef6a27244994a2ec6b766b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399786"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 構造体

`CDaoParameterInfo`構造体には、データ アクセス オブジェクト (DAO) に対して定義されているパラメーターのオブジェクトに関する情報が含まれています。

## <a name="syntax"></a>構文

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
パラメーター オブジェクトの一意名します。 詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

*m_nType*<br/>
パラメーター オブジェクトのデータ型を示す値。 使用可能な値の一覧を参照してください、 *m_nType*のメンバー、 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。 詳細については、「型のプロパティ」DAO ヘルプのトピックを参照してください。

*m_varValue*<br/>
格納され、パラメーターの値を[COleVariant](../../mfc/reference/colevariant-class.md)オブジェクト。

## <a name="remarks"></a>Remarks

プライマリとセカンダリの上への参照情報がによって返される方法を示すため、 [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)クラスのメンバー関数`CDaoQueryDef`します。

MFC は、DAO クラスでオブジェクトのパラメーターをカプセル化しません。 クエリ定義オブジェクトの基になる MFC`CDaoQueryDef`オブジェクトは、パラメーターをパラメーター コレクションに格納します。 パラメーター オブジェクトにアクセスする、 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)オブジェクトをクエリ定義オブジェクトの`GetParameterInfo`メンバー関数は、特定のパラメーター名またはパラメーターのコレクションへのインデックス。 使用することができます、 [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)メンバー関数と組み合わせて`GetParameterInfo`パラメーター コレクションをループ処理します。

によって取得される情報、 [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)にメンバー関数が格納されている、`CDaoParameterInfo`構造体。 呼び出す`GetParameterInfo`クエリ定義オブジェクトをパラメーター コレクションを持つパラメーター オブジェクトを格納します。

> [!NOTE]
>  取得または設定パラメーターの値のみを使用する場合、 [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)と[パラメータ](../../mfc/reference/cdaorecordset-class.md#setparamvalue)クラスのメンバー関数`CDaoRecordset`します。

`CDaoParameterInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoParameterInfo`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef クラス](../../mfc/reference/cdaoquerydef-class.md)
