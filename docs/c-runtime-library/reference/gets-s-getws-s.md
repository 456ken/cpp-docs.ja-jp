---
title: gets_s、_getws_s
ms.date: 11/04/2016
apiname:
- _getws_s
- gets_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getws_s
- gets_s
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
ms.openlocfilehash: f71fafceaf1974bc5ff736ff175a67cf6c924ee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157657"
---
# <a name="getss-getwss"></a>gets_s、_getws_s

行を取得、 **stdin**ストリーム。 これらの [gets および _getws](../../c-runtime-library/gets-getws.md) のバージョンは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」(CRT のセキュリティ機能) で説明されているように、セキュリティが強化されています。

## <a name="syntax"></a>構文

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
入力文字列の格納場所。

*sizeInCharacters*<br/>
バッファーのサイズ。

## <a name="return-value"></a>戻り値

返します*バッファー*成功した場合。 エラーが発生した場合またはファイルの終端に達した場合は、**NULL** ポインターを返します。 どちらが発生したかを確認するには、 [ferror](ferror.md) または [feof](feof.md) を使用します。

## <a name="remarks"></a>Remarks

**Gets_s**関数は、標準入力ストリームから行を読み取ります**stdin**に格納*バッファー*します。 行は、最初の改行文字 ('\n') までのすべての文字 (改行文字を含む) で構成されます。 **gets_s** null 文字 ('\0') で、行を返す前に、改行文字を置き換えます。 これに対し、 **fgets_s**関数は、改行文字を保持します。

先頭に null 文字が格納されているファイルの終端文字の場合は、最初の文字を読み取る*バッファー*と**NULL**が返されます。

**_getws_s**のワイド文字バージョンは、 **gets_s**; の引数と戻り値はワイド文字列です。

場合*バッファー*は**NULL**または*sizeInCharacters*が 0 未満か、バッファーが小さすぎて入力行と終端の null を含める場合は、これらの関数を呼び出す」の説明に従って、無効なパラメーター ハンドラー[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 これらの関数を返すかどうかは、引き続き実行が許可された、 **NULL**に errno を設定および**ERANGE**します。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> または \<wchar.h>|

ユニバーサル Windows プラットフォーム (UWP) アプリでは、コンソールがサポートされていません。 コンソールに関連付けられている標準ストリームのハンドル**stdin**、 **stdout**、および**stderr**、C ランタイム関数が UWP アプリで使用する前にリダイレクトする必要があります. 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets、fgetws](fgets-fgetws.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
