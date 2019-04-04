---
title: レコード フィールド エクスチェンジ (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: f612f4be726707681ffbddff88ccc6b8a672e427
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522409"
---
# <a name="record-field-exchange-rfx"></a>レコード フィールド エクスチェンジ (RFX)

MFC ODBC データベース クラスは、データ ソース間のデータの移動を自動化し、 [recordset](../../data/odbc/recordset-odbc.md)オブジェクト。 クラスを派生する[CRecordset](../../mfc/reference/crecordset-class.md)レコード フィールド エクス (チェンジ RFX) メカニズムによってデータが転送される、バルク行フェッチを使用しないでください。

> [!NOTE]
>  派生にバルク行フェッチを実装している場合`CRecordset`クラス、データを転送するには使用、バルク レコード フィールド エクス チェンジ (Bulk RFX) メカニズムをフレームワーク。 詳細については、[レコード セット: レコードのフェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)を参照してください。

Rfx 関数は、ダイアログ データ エクス (チェンジ DDX) と似ています。 データ ソースとレコード セットのフィールド データ メンバーのデータを移動するには、レコード セットの複数の呼び出しが必要です[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)フレームワーク間の関数の相互作用と[ODBC](../../data/odbc/odbc-basics.md). RFX メカニズムがタイプ セーフし、などの ODBC 関数を呼び出すことの作業を保存する`::SQLBindCol`します。 DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

RFX は意識する必要はほとんどの場合です。 MFC アプリケーション ウィザードを使用して、レコード セット クラスを宣言したかどうかまたは**クラスの追加**(」の説明に従って[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md))、RFX がそれらに自動的に組み込まれています。 レコード セット クラスは基底クラスから派生する必要があります`CRecordset`framework によって提供されます。 MFC アプリケーション ウィザードでは、最初のレコード セット クラスを作成できます。 **クラスを追加**必要に応じて、他のレコード セット クラスを追加することができます。 詳細と例については、[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)を参照してください。

場合に、3 つのケースで少量の rfx 関数のコードを追加する必要があります手動で。

- パラメーター化クエリを使用します。 詳細については、[レコード セット: レコード セット (ODBC) をパラメーター化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)を参照してください。

- 結合 (2 つ以上のテーブルの列の 1 つのレコード セットの使用) を実行します。 詳細については、[レコード セット: 結合 (ODBC) を実行する](../../data/odbc/recordset-performing-a-join-odbc.md)を参照してください。

- データ列を動的にバインドします。 これは、パラメーター化よりもまれです。 詳細については、[レコード セット: データ列を動的にバインド (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)を参照してください。

RFX の高度な知識が必要な場合は、[レコード フィールド エクス チェンジ: RFX のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)を参照してください。

次のトピックでは、レコード セット オブジェクトの使用の詳細について説明します。

- [レコード フィールド エクスチェンジ: RFX の使い方](../../data/odbc/record-field-exchange-using-rfx.md)

- [レコード フィールド エクスチェンジ: RFX 関数の使い方](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [レコード フィールド エクスチェンジ: RFX の動作のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC コンシューマーします。](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[[データベース サポート] (MFC アプリケーション ウィザード)](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)