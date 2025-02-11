---
title: '方法: winmdidl.exe と midlrt.exe を使用して、Windows メタデータから .h ファイルを作成する'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: 8288fc11fd53fdef423a57d0faefbaa7c06326aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500430"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>方法: winmdidl.exe と midlrt.exe を使用して、Windows メタデータから .h ファイルを作成する

winmdidl.exe と midlrt.exe によって、ネイティブ C++ コードと Windows ランタイム コンポーネントの間の COM レベルの相互作用が可能になります。 winmdidl.exe は、入力として Windows ランタイム コンポーネントのメタデータが含まれる .winmd ファイル受け取り、IDL ファイルを出力します。 midlrt.exe は、IDL ファイルを C++ コードで使用できるヘッダー ファイルに変換します。 両方のツールはコマンド ラインで実行されます。

これらのツールは、次の 2 つの主要シナリオで使用します。

- Windows ランタイム テンプレート ライブラリ (WRL) を使用して作成された C ++ アプリケーションが、カスタム Windows ランタイム コンポーネントを使用できるようにする、カスタム IDL ファイルとヘッダー ファイルの作成。

- Windows ランタイム コンポーネントでのユーザー定義のイベントの種類用のプロキシおよびスタブ ファイルの生成。 詳細については、「 [Windows ランタイムコンポーネントのカスタムイベントとイベントアクセサー](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components)」を参照してください。

これらのツールは、カスタム .winmd ファイルを解析する場合にのみ必要です。 Windows オペレーティング システムのコンポーネント用の .idl および .h ファイルは、既に生成されます。 Windows 8.1 の既定では、これらのファイルは、Kits\8.1\Include\winrt\\(x86) \windows にあります。

## <a name="location-of-the-tools"></a>ツールの場所

既定では、[Windows 8.1、winmdidl と midlrt は C:\Program Files (x86) \Windows Kits\8.1\\にあります。 ツールのバージョンは、\bin\x86\ および \bin\x64\ フォルダーでも使用できます。

## <a name="winmdidl-command-line-arguments"></a>winmdidl のコマンド ライン引数

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
winmdidl の著作権メッセージとバージョン番号のコンソール表示を防ぎます。

**/suppressversioncheck**<br/>
使用しません。

**/時刻**<br/>
コンソール出力に総実行時間を表示します。

**/outdir:** <em>ディレクトリ</em><br/>
出力ディレクトリを指定します。 パスに空白が含まれる場合は、引用符を使用します。 既定の出力ディレクトリは *\<ドライブ >* : \Users\\ *\<ユーザー名 >* \AppData\Local\VirtualStore\Program Files (x86) \Microsoft VisualStudio 12.0\\します。

**/バナー:** <em>ファイル</em><br/>
生成された .idl ファイルの先頭にある既定の著作権メッセージと winmdidl のバージョン番号に付加するカスタム テキストを含むファイルを指定します。 パスに空白が含まれる場合は、引用符を使用します。

**/utf8**<br/>
ファイルを UTF-8 として書式設定します。

*Winmdfile*<br/>
解析する .winmd ファイルの名前。 パスに空白が含まれる場合は、引用符を使用します。

## <a name="midlrt-command-line-arguments"></a>midlrt のコマンド ライン引数

「 [Midlrt と Windows ランタイムコンポーネント」を](/windows/win32/Midl/midlrt-and-windows-runtime-components)参照してください。

## <a name="examples"></a>使用例

次の例に、Visual Studio x86 コマンド プロンプトでの winmdidl コマンドを示します。 これは、出力ディレクトリと、生成された .idl ファイルに追加する特別な見出しテキストが含まれるファイルを指定します。

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

次の例に、操作が成功したことを示す winmdidl からのコンソール表示を示します。

**C:\users\giraffe\documents\\\Test_for_winmdidl.idl の生成**

次に、midlrt が生成された IDL ファイルに実行されます。 **Metadata_dir**引数が .idl ファイルの名前の後に指定されていることに注意してください。 \WinMetadata\ のパスが必要です。これは windows.winmd の場所です。

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Remarks

winmdidl 操作からの出力ファイルは入力ファイルと同じ名前ですが、ファイル名拡張子が .idl です。

WRL からアクセスされる Windows ランタイム コンポーネントを開発している場合は、.idl および .h ファイルが各ビルドで生成されるように、winmdidl.exe と midlrt.exe をビルド後のステップとして実行するように指定できます。 例については、「 [Windows ランタイムコンポーネントでのイベントの発生](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components)」を参照してください。