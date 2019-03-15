---
title: PgoAutoSweep
ms.date: 03/14/2018
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 2d9804e5ce90663d44ac389ab4f71d10290e6470
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827268"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` ファイルにプロファイルの現在のカウンター情報を保存し、カウンターをリセットします。 プロファイル ガイド付き最適化の実行中のプログラムから .pgc ファイル最適化のビルドの後で使用するすべてのプロファイル データを記述するトレーニング中に、関数を使用します。

## <a name="syntax"></a>構文

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>パラメーター

*name*<br/>
保存されている .pgc ファイルの識別文字列。

## <a name="remarks"></a>Remarks

呼び出すことができます`PgoAutoSweep`から、アプリケーションを保存し、アプリケーションの実行中に任意の時点で、プロファイル データをリセットします。 インストルメントされたビルドで`PgoAutoSweep`は現在のプロファイル データをキャプチャ、ファイルに保存、およびプロファイル カウンターをリセットします。 呼び出し元のと同じ、 [pgosweep](pgosweep.md)特定の時点で、実行可能ファイル コマンド。 最適化されたビルドでは、`PgoAutoSweep`は行いません。

カウンター データを保存されたプロファイルがという名前のファイルに配置*base_name*-*名前*!*値*.pgc、場所*base_name*は、実行可能ファイルの基本名*名前*に渡されたパラメーター `PgoAutoSweep`、および*値*一意の値、ファイル名の競合を防ぐために、通常は連番です。

によって作成された .pgc ファイル`PgoAutoSweep`最適化された実行可能ファイルの作成に使用される .pgd ファイルにマージする必要があります。 使用することができます、 [pgomgr](pgomgr.md)マージを実行するコマンド。

最適化のビルド中を使用して、リンカーにマージされた .pgd ファイルの名前を渡すことができます、 **PGD =**_filename_への引数、 [/USEPROFILE](reference/useprofile.md)リンカー オプション、または非推奨を使用して **/PGD**リンカー オプション。 という名前のファイルには、.pgc ファイルをマージするかどうかは*base_name*.pgd、する必要はありません、コマンドラインで、ファイル名を指定するため、リンカーが既定でこのファイル名を取得します。

`PgoAutoSweep`機能は、スレッド セーフの設定は、インストルメント化されたビルドを作成するときに指定します。 既定の設定を使用するか、指定した場合、 **noexact は、** への引数、 [/GENPROFILE または/FASTGENPROFILE]()リンカー オプション、呼び出し`PgoAutoSweep`スレッド セーフではありません。 **EXACT**引数作成スレッド セーフでありより正確なが低速でインストルメント化された実行可能ファイルです。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

実行可能ファイルは、リンクされたライブラリに pgobootrun.lib ファイルを含める必要があります。 このファイルは、サポートされている各アーキテクチャの VC ライブラリ ディレクトリに、Visual Studio のインストールに含まれます。

## <a name="example"></a>例

使用して次の例`PgoAutoSweep`に 2 つ作成します。実行中にさまざまな時点の PGC ファイル。 最初にまでのランタイム動作を説明するデータが含まれています`count`が 3、2 番目にアプリケーションの終了直前までこのポイントの後に収集されたデータが含まれています。

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

開発者コマンド プロンプトで、このコマンドを使用してオブジェクト ファイルにコードをコンパイルします。

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

このコマンドを使用してトレーニング用にインストルメントされたビルドを生成します。

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

トレーニング データをキャプチャするインストルメント化された実行可能ファイルを実行します。 データの出力への呼び出しによって`PgoAutoSweep`pgoautosweep func1 という名前のファイルに保存されます。 1.pgc と pgoautosweep func2! 1.pgc。 実行時にこのようプログラムの出力になります。

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

実行して、プロファイルのトレーニング データベースに保存されたデータをマージ、 **pgomgr**コマンド。

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

このコマンドの出力は、次のようになります。

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

今すぐこのトレーニング データを使用して、最適化されたビルドを生成することができます。 このコマンドを使用して、最適化された実行可能ファイルを作成します。

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>関連項目

[ガイド付き最適化のプロファイル](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
