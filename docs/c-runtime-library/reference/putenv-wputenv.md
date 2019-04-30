---
title: _putenv、_wputenv
ms.date: 11/04/2016
apiname:
- _putenv
- _wputenv
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 952a4d62f6ceb6b689091ac09f6ca338d0b10864
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357890"
---
# <a name="putenv-wputenv"></a>_putenv、_wputenv

環境変数を作成、変更、または削除します。 これらの関数にはセキュリティが強化されたバージョンがあります。「[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)」をご覧ください。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>パラメーター

*envstring*<br/>
環境文字列定義。

## <a name="return-value"></a>戻り値

成功した場合は 0、エラーの場合は-1 を返します。

## <a name="remarks"></a>Remarks

**_Putenv**関数は、新しい環境変数を追加します。 または、既存の環境変数の値を変更します。 環境変数は、プロセス (たとえば、プログラムにリンクされるライブラリの既定の検索パス) が実行される環境を定義します。 **_wputenv**のワイド文字バージョンです **_putenv**、 *envstring*引数 **_wputenv**はワイド文字列です。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*引数は形式の文字列へのポインターである必要があります*varname*=*value_string*ここで、 *varname*は追加または変更するには、環境変数の名前と*value_string*は変数の値です。 場合*varname* 、環境の一部では既にその値が置き換え*value_string*そうしないと、新しい*varname*変数とその*value_string。* 値が環境に追加されます。 環境から変数を削除するには、空を指定することによって*value_string*、またはのみを指定して、つまり、 *varname*=。

**_putenv**と **_wputenv**現在のプロセスに対してローカルの環境のみに影響は、それらを使用して、コマンド レベルの環境を変更することはできません。 つまり、これらの関数は、ランタイム ライブラリからアクセスできるデータ構造体だけを対象とし、プロセス用にオペレーティング システムで作成された環境 "セグメント" は参照しません。 現在のプロセスが終了すると、環境は、呼び出し元プロセス (ほとんどの場合、オペレーティング システムのレベル) のレベルに戻ります。 ただし、によって作成された新しいプロセスに変更された環境を渡すことができます **_spawn**、 **_exec**、または**システム**、し、これらの新しいプロセスによって追加された新しい項目を取得します。**_putenv**と **_wputenv**します。

環境のエントリを直接変更しないでください。 代わりに、 **_putenv**または **_wputenv**を変更します。 具体的には、直接の要素の解放、 **_environ:operator[]** グローバル配列は無効なメモリが、現在対処中に生じる可能性があります。

**getenv**と **_putenv**グローバル変数を使用して **_environ** ; して環境テーブルにアクセスするには **_wgetenv**と **_wputenv**使用 **_wenviron**します。 **_putenv**と **_wputenv**の値を変更する可能性があります **_environ**と **_wenviron**、したがって無効化、 **_envp**引数を**メイン**と **_wenvp**引数**wmain**します。 そのため、使用しても安全は **_environ**または **_wenviron**環境情報にアクセスします。 関係の詳細については **_putenv**と **_wputenv**グローバル変数を参照してください。 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)します。

> [!NOTE]
> **_Putenv**と**系**系関数はスレッド セーフではされません。 **_putenv**中に文字列ポインターを返すことができます **_putenv**がランダムにエラーの原因と、文字列を変更します。 これらの関数の呼び出しが同期されていることを確認する必要があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

使用する方法の例については **_putenv**を参照してください[getenv、_wgetenv](getenv-wgetenv.md)します。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、 _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
