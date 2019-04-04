---
title: ATL データベース クラス (OLE DB テンプレート)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 4304c350ce6a9303a7542809fa85fb0cd2560031
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522079"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL データベース クラス (OLE DB テンプレート)

Microsoft では、OLE DB では、一連のさまざまな情報源や形式のデータに同じ方法でアクセスを提供する COM インターフェイスの実装がいくつか提供します。  OLE DB は正式に非推奨とされます。このドキュメントでは、レガシ コードを保持している開発者のためです。 新しいアプリケーションは、ODBC を使用して、SQL データ ソースに接続する必要があります。

OLE DB テンプレートは、OLE DB データベース テクノロジを使いやすく、一般的に使用される OLE DB インターフェイスの多くを実装するクラスを提供することで、ATL の C++ テンプレートです。

このテンプレート ライブラリには、2 つの部分が含まれています。

- [OLE DB コンシューマー テンプレート](../data/oledb/ole-db-consumer-templates-cpp.md)OLE DB (コンシューマー) のクライアント アプリケーションを実装するために使用します。

- [OLE DB プロバイダー テンプレート](../data/oledb/ole-db-provider-templates-cpp.md)OLE DB サーバー (プロバイダー) アプリケーションを実装するために使用します。

さらに、 [OLE DB コンシューマー属性](../windows/ole-db-consumer-attributes.md)OLE DB コンシューマーを作成する便利な手段を提供します。 OLE DB 属性では、作業用の OLE DB コンシューマーを作成する OLE DB コンシューマー テンプレートに基づくコードを挿入します。

MFC ライブラリに 1 つのクラスが含まれているメモ[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)コントロールでのデータベース レコードを表示します。 ビューが、フォーム ビューに直接接続されている、`CRowset`オブジェクトし、のフィールドが表示されます、`CRowset`ダイアログ テンプレートのコントロール内のオブジェクト。

詳細については、[OLE DB プログラミング](../data/oledb/ole-db-programming.md)と[OLE DB プログラマ ガイド](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマーの作成](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[OLE DB プロバイダーの作成](../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB プロバイダー テンプレート リファレンス](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB テンプレート サンプル](https://github.com/Microsoft/VCSamples)