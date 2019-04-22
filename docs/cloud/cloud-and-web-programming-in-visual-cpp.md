---
title: Visual C++ でのクラウドおよび Web プログラミング
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 33431a8f8660af683ed2e39e10811c22fe2f4fcc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773087"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Visual C++ でのクラウドおよび Web プログラミング

C++ では、Web とクラウドに接続するためのいくつかの方法があります。

## <a name="cloud-programming-options"></a>クラウドのプログラミングのオプション

- [Microsoft Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

  Windows Azure モバイル サービスに接続するユニバーサル Windows プラットフォーム (UWP) アプリまたは Windows デスクトップ アプリで使用できるネイティブ Api を提供します。 Web サイトの例のほとんどは C# を使用していますが、C++ も使用できます。 詳細については、「[クイック スタート:C++ を使用してモバイル サービスの追加](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx)します。

- [C++ 用 Microsoft Azure Storage クライアント ライブラリ](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  C++ 用 Azure Storage クライアント ライブラリには、次の機能など、Azure storage を操作するための包括的な API が用意されています。

  - 作成、読み取り、削除、および blob コンテナー、テーブル、およびキューを一覧表示します。
  - 作成、読み取り、削除、プラス記号の一覧とコピー blob が blob の範囲を読み書きします。
  - Insert、delete、replace、merge、および Azure テーブル エンティティを照会します。
  - エンキューし、Azure のキューにメッセージをデキューします。
  - コンテナー、blob、テーブル、キュー、および遅延ボックスの一覧し、エンティティの遅延クエリ

- [OneDrive API](https://dev.onedrive.com/README.htm)

  OneDrive API は、一連のファイルと Office 365 と SharePoint Server 2016 でのフォルダーにアプリケーションを接続する HTTP サービスを提供します。

- [C++ REST SDK (Codename "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  REST サービスと対話するためには、最近、クロスプラット フォームで、非同期 API を提供します。

  - JSON ドキュメントの解析とシリアル化の組み込みサポートを備えた、任意の HTTP サーバーに対する REST 呼び出しを実行します。
  - OAuth 1 と 2 は、ローカル リダイレクト リスナーを含むをサポートしています
  - リモート サービスに対して Websocket 接続を作成します。
  - 完全に非同期タスクなどの組み込みの threadpool PPL に基づく API

  Windows デスクトップ (7 以降)、Windows Server (2012 以降)、ユニバーサル Windows プラットフォーム、Linux、OSX、Android、および iOS をサポートしています。

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  System.Web 名前空間にある同じ名前の .NET Framework クラスでモデル化された Windows ランタイムの HTTP クライアント クラスです。 `HttpClient` は、HTTP 経由の非同期アップロードとダウンロード、およびパイプラインにカスタム HTTP ハンドラーを挿入するためのパイプライン フィルターを完全にサポートします。 Windows SDK には、メーター付きネットワークや OAuth 認証用のサンプル フィルターが含まれています。 ユニバーサル Windows プラットフォームのみを対象とするアプリをお勧めを使用すること、`Windows::Web:HttpClient`クラス。

- [IXMLHTTPRequest2 インターフェイス](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  問題の GET、PUT、およびその他の HTTP コマンドを HTTP 経由でインターネットに接続する Windows デスクトップ アプリまたは Windows ランタイム アプリで使用することができます、ネイティブな COM インターフェイスを提供します。 詳細については、「[チュートリアル:タスクおよび XML HTTP 要求を使用して接続](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)します。

- [Windows インターネット (WinInet)](/windows/desktop/WinInet/portal)

  Windows デスクトップ アプリでインターネットに接続するために使用できる Windows API。

## <a name="see-also"></a>関連項目

[Visual C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[ネットワークと web サービス](/windows/uwp/networking/)
