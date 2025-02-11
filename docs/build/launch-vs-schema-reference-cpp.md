---
title: と json スキーマ参照 (C++) を起動します。
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 362a329289107f74cca2f20af62c8a28b4192575
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69978462"
---
# <a name="launchvsjson-schema-reference-c"></a>と json スキーマ参照 (C++) を起動します。

デバッグパラメーターを構成するには、の*起動. と json*ファイルを使用します。 ファイルを作成します。 **ソリューションエクスプローラー**で実行可能ファイルを右クリックし、 **[デバッグ設定と起動設定]** を選択します。 プロジェクトに最も近いオプションを選択し、次のプロパティを使用して必要に応じて構成を変更します。

## <a name="default-properties"></a>既定のプロパティ

||||
|-|-|-|
|**Property**|**Type**|**説明**|
|`name`|string|[デバッグターゲット] ドロップダウンでエントリの名前を指定します。|
|`type`|string|プロジェクトが dll または .exe (既定では .exe) であるかどうかを指定します。|
|`project`|string|プロジェクトファイルへの相対パスを指定します。|
|`projectTarget`|string|ビルド`project`時に呼び出されるオプションのターゲットを指定します。 これ`projectTarget`は既に存在し、 **[デバッグターゲット]** ドロップダウンの名前と一致している必要があります。|
|`debugType`|string|コードの種類 (ネイティブ、マネージ、または混合) に応じてデバッグモードを指定します。 このパラメーターが設定されていない場合は、自動的に検出されます。 使用できる値: "native"、"managed"、"mixed"。|
|`inheritEnvironments`|array|複数のソースから継承された環境変数のセットを指定します。 CMakeSettings. json や Cmakesettings. json などのファイルでいくつかの変数を定義し、デバッグコンテキストで使用できるようにすることができます。|
|`args`|array|起動されるプログラムに渡されるコマンドライン引数を指定します。|
|`currentDir`|string|ビルドターゲットへの完全なディレクトリパスを指定します。 このパラメーターが設定されていない場合は、自動的に検出されます。|
|`noDebug`|boolean|起動されたプログラムをデバッグするかどうかを指定します。 このパラメーターの既定値は、 `false`指定されていない場合はです。|
|`stopOnEntry`|boolean|プロセスが起動し、デバッガーがアタッチされるとすぐに中断するかどうかを指定します。 このパラメーターの既定値は`false`です。|
|`remoteMachine`|string|プログラムを起動するリモートコンピューターの名前を指定します。|
|`env`|array| カスタム環境変数のキーと値の一覧を指定します。 env: {"myEnv": "Myenv"}。|
|`portName`|string|実行中のプロセスにアタッチするときのポート名を指定します。|
|`buildConfigurations`|array| 構成を適用するビルドモードの名前を指定するキーと値のペア。 たとえば、また`Debug`は`Release` 、選択したビルドモードに従って使用する構成などです。

## <a name="c-linux-properties"></a>C++Linux のプロパティ

||||
|-|-|-|
|**Property**|**Type**|**説明**|
|`program`|string|リモートコンピューター上のプログラム実行可能ファイルへの完全パスです。 Cmake を使用する場合は`${debugInfo.fullTargetPath}` 、このフィールドの値としてマクロを使用できます。|
|`processId`|整数|デバッガーをアタッチするプロセス ID (省略可能)。|
|`sourceFileMap`|オブジェクト|デバッグエンジンに渡されるオプションのソースファイルマッピング。 形式: `{ "\<Compiler source location>": "\<Editor source location>" }`また`{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`は。 例: `{ "/home/user/foo": "C:\\foo" }`また`{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`は。 「[ソースファイルマップのオプション](#source_file_map_options)」を参照してください。|
|`additionalProperties`|string|SourceFileMapOptions の1つ。 (以下を参照してください。)|
|`MIMode`|string|MIDebugEngine が接続する MI が有効なコンソールデバッガーの種類を示します。 使用できる値は "gdb"、"lldb" です。|
|`args`|array|プログラムに渡されるコマンドライン引数。|
|`environment`|array|プログラムの環境に追加する環境変数。 例: [{"name": "squid", "value": "貝"}]。|
|`targetArchitecture`|string|デバッグ対象のアーキテクチャ。 このパラメーターが設定されていない場合は、自動的に検出されます。 使用できる値は、x86、arm、arm64、mips、x64、amd64、x86_64 です。|
|`visualizerFile`|string|このプロセスをデバッグするときに使用する natvis ファイル。 このオプションは、GDB の整形出力と互換性がありません。 この設定を使用する場合は、"showDisplayString" を参照してください。|
|`showDisplayString`|boolean|VisualizerFile を指定すると、showDisplayString によって表示文字列が有効になります。 このオプションをオンにすると、デバッグ中にパフォーマンスが低下する可能性があります。|
|`remoteMachineName`|string|Gdb とデバッグするプログラムをホストするリモート Linux コンピューター。 新しい Linux マシンを追加するには、接続マネージャーを使用します。 Cmake を使用する場合は`${debugInfo.remoteMachineName}` 、このフィールドの値としてマクロを使用できます。|
|`cwd`|string|リモートコンピューター上のターゲットの作業ディレクトリ。 Cmake を使用する場合は`${debugInfo.defaultWorkingDirectory}` 、このフィールドの値としてマクロを使用できます。 既定値は、 *Cmakelists .txt*ファイルでオーバーライドされない限り、リモートワークスペースのルートです。|
|`miDebuggerPath`|string|MI が有効になっているデバッガー (gdb など) へのパス。 指定されていない場合は、まず、デバッガーのパスを検索します。|
|`miDebuggerServerAddress`|string|接続先となる MI 対応のデバッガーサーバーのネットワークアドレス。 例: localhost: 1234。|
|`setupCommands`|array|基になるデバッガーを設定するために実行する1つ以上の GDB/LLDB コマンド。 例 : `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`。 「[セットアップコマンドの起動](#launch_setup_commands)」を参照してください。|
|`customLaunchSetupCommands`|array|指定されている場合、これにより、他のいくつかのコマンドでターゲットを起動するために使用される既定のコマンドが置き換えられます。 たとえば、ターゲットプロセスにアタッチするために、これを "-target-attach" にすることができます。 空のコマンドリストによって起動コマンドが何も置き換えられません。これは、デバッガーがコマンドラインオプションとして起動オプションを提供している場合に便利です。 例 : `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`。|
|`launchCompleteCommand`|string|デバッガーが完全にセットアップされた後に実行するコマンド。ターゲットプロセスを実行します。 使用できる値は、"exec-run"、"exec-continue"、"None" です。 既定値は "exec-run" です。|
|`debugServerPath`|string|起動するデバッグサーバーの完全パス (省略可能)。 既定値は null です。|
|`debugServerArgs`|string|省略可能なデバッグサーバー引数。 既定値は null です。|
|`filterStderr`|boolean|サーバーによって開始されたパターンの stderr ストリームを検索し、stderr をデバッグ出力に記録します。 既定値は `false` です。|
|`coreDumpPath`|string|指定したプログラムのコアダンプファイルへの完全パス (省略可能)。 既定値は null です。|
externalConsole|boolean|True の場合、デバッグ対象のコンソールが起動されます。 の`false`場合、コンソールは起動されません。 既定値は `false` です。 注: このオプションは、技術的な理由によっては無視されます。|
|`pipeTransport`|string|存在する場合、これにより、デバッガーは、Visual Studio と MI 対応のデバッガー (gdb など) の間で標準入出力をリレーするパイプとして、別の実行可能ファイルを使用してリモートコンピューターに接続するように指示されます。 使用可能な値: 1 つ以上の[パイプトランスポートオプション](#pipe_transport_options)。|


## <a name="launch_setup_commands"></a>セットアップコマンドを起動する

プロパティと共`setupCommands`に使用します。

||||
|-|-|-|
|`text`|string|実行するデバッガーコマンド。|
|`description`|string|コマンドの説明 (省略可能)。|
|`ignoreFailures`|boolean|True の場合、コマンドからの失敗は無視されます。 既定値は `false` です。|

## <a name = "pipe_transport_options"></a>パイプトランスポートオプション

プロパティと共`pipeTransport`に使用します。

||||
|-|-|-|
|`pipeCwd`|string|パイププログラムの作業ディレクトリへの絶対パス。|
|`pipeProgram`|string|実行する完全修飾パイプコマンド。|
|`pipeArgs`|array|接続を構成するためにパイププログラムに渡されるコマンドライン引数。|
|`debuggerPath`|string|ターゲットコンピューター上のデバッガーへの完全パス (例:/usr/bin/gdb。)|
|`pipeEnv`|オブジェクト|パイププログラムに渡される環境変数。|
|`quoteArgs`|boolean|個々の引数に文字 (スペースやタブなど) が含まれている場合は、引用符で囲む必要があります。 の`false`場合、デバッガーコマンドは自動的に引用符で囲まれなくなります。 既定値は `true` です。|

## <a name="source_file_map_options"></a>ソースファイルマップのオプション

`sourceFileMap`プロパティと共にを使用します。

||||
|-|-|-|
|`editorPath`|string|エディターが検索するソースコードの場所。|
|`useForBreakpoints`|boolean|ブレークポイントを設定するときは、このソースマッピングを使用する必要があります。 の`false`場合、ブレークポイントの設定にはファイル名と行番号のみが使用されます。 の`true`場合、ブレークポイントは、このソースマッピングが使用されている場合にのみ、ファイルと行番号への完全パスを使用して設定されます。 それ以外の場合は、ブレークポイントを設定するときに、ファイル名と行番号のみが使用されます。 既定値は `true` です。|
