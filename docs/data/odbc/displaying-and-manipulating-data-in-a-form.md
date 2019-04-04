---
title: フォームでのデータの表示と操作
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 1694d9cbc770e02c550891fc83c1cc0a9f64824a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517794"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>フォームでのデータの表示と操作

多くのデータ アクセス アプリケーションでは、データを選択し、フォームのフィールドに表示します。 Database クラス[CRecordView](../../mfc/reference/crecordview-class.md)できます、 [CFormView](../../mfc/reference/cformview-class.md)レコード セット オブジェクトに直接接続されているオブジェクト。 レコード ビューを使用して[ダイアログ データ エクス (チェンジ DDX)](../../mfc/dialog-data-exchange-and-validation.md)レコード セットから、フォーム上のコントロールに現在のレコードのフィールドの値を移動して、更新情報は、レコード セットに移動します。 レコード セットは、データ ソースのフィールド データ メンバーと、テーブル内の対応する列の間でデータを移動、レコード フィールド エクス (チェンジ RFX) を使用します。

MFC アプリケーション ウィザードを使用するまたは**クラスの追加**(」の説明に従って[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) を組み合わせてビュー クラスとその関連するレコード セット クラスを作成します。

レコード ビューとそのレコード セットは、ドキュメントを閉じるときに破棄されます。 レコード ビューの詳細については、[レコード ビュー](../../data/record-views-mfc-data-access.md)を参照してください。 RFX の詳細については、[レコード フィールド エクス チェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)を参照してください。

## <a name="see-also"></a>関連項目

[ODBC と MFC](../../data/odbc/odbc-and-mfc.md)