---
title: コンシューマー ウィザードで生成されたメソッド
ms.date: 11/04/2016
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 60ca0af25a0556c4a3d42d91ba3b0c52daa5f530
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409136"
---
# <a name="consumer-wizard-generated-methods"></a>コンシューマー ウィザードで生成されたメソッド

**ATL OLE DB コンシューマー ウィザード**と**MFC アプリケーション ウィザード**を把握しておく必要があります、特定の関数を生成します。 いくつかのメソッド実装方法が異なります属性付きプロジェクトでは、いくつかの注意事項があるため各ケースは、以下について説明します。 挿入されたコードを表示する方法については、「 [挿入されたコードのデバッグ](/visualstudio/debugger/how-to-debug-injected-code)」を参照してください。

- `OpenAll` データ ソースの行セットを開き、利用可能な場合は、ブックマークをオンにします。

- `CloseAll` 開いているすべての行セットを終了し、すべてのコマンドの実行を解放します。

- `OpenRowset` によって呼び出される`OpenAll`をコンシューマーの行セットまたは行セットを開きます。

- `GetRowsetProperties` 設定するプロパティを設定すると、行セットのプロパティへのポインターを取得します。

- `OpenDataSource` 指定した、初期化文字列を使用してデータ ソースを開き、**データ リンク プロパティ** ダイアログ ボックス。

- `CloseDataSource` 適切な方法でデータ ソースを閉じます。

## <a name="openall-and-closeall"></a>OpenAll and CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

次の例は、呼び出す方法を示しています。`OpenAll`と`CloseAll`繰り返し、同じコマンドを実行するとします。 コード例を比較[ccommand::close](../../data/oledb/ccommand-close.md)を呼び出すバリエーションを示す`Close`と`ReleaseCommand`の代わりに`CloseAll`します。

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>Remarks

定義する場合、`HasBookmark`メソッド、`OpenAll`設定するコード、`DBPROP_IRowsetLocate`プロパティは、プロバイダーは、そのプロパティをサポートしている場合にのみ、このメソッドを定義してください。

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` コンシューマーの行セットまたは行セットを開くには、このメソッドを呼び出します。 通常を呼び出す必要はありません`OpenRowset`複数データ ソース/セッション/行セットを使用する場合を除き、します。 `OpenRowset` コマンドまたはテーブル クラスのヘッダー ファイルで宣言されます。

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

属性は、異なる方法でこのメソッドを実装します。 このバージョンでは、セッション オブジェクトおよびその db_command で指定されたコマンド文字列を既定値は、別のアカウントを渡すことができますが、コマンド文字列を受け取ります。 定義する場合、`HasBookmark`メソッド、`OpenRowset`設定するコード、`DBPROP_IRowsetLocate`プロパティは、プロバイダーは、そのプロパティをサポートしている場合にのみ、このメソッドを定義してください。

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

このメソッドは、行セットのプロパティ セットへのポインターを取得しますこのポインターを使用するにはなどのプロパティを設定する`DBPROP_IRowsetChange`します。 `GetRowsetProperties` 以下を使用、ユーザー レコード クラスにします。 追加の行セット プロパティを設定するには、このコードを変更することができます。

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>Remarks

グローバル定義しないでください`GetRowsetProperties`メソッドのいずれかの競合がため、ウィザードによって定義されます。 これは、ウィザードで生成されたテンプレートおよび属性のプロジェクトで得られるメソッド属性は、このコードを挿入はありません。

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource および CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Remarks

ウィザードは、メソッドを定義します`OpenDataSource`と`CloseDataSource`;。`OpenDataSource`呼び出し[cdatasource::openfrominitializationstring](../../data/oledb/cdatasource-openfrominitializationstring.md)します。

## <a name="see-also"></a>関連項目

[ウィザードを使用した OLE DB コンシューマーの作成](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)