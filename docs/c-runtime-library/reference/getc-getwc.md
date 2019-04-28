---
title: getc、getwc
ms.date: 11/04/2016
apiname:
- getwc
- getc
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
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: bbaee79eac6802959a11f7f1ba30eaf590ecf2f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331871"
---
# <a name="getc-getwc"></a>getc、getwc

ストリームから単一の文字を読み取ります。

## <a name="syntax"></a>構文

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*stream*<br/>
入力ストリーム。

## <a name="return-value"></a>戻り値

読み取られた文字を返します。 読み取りエラーまたはファイルの終わりの条件を示す**getc**返します**EOF**と**getwc**返します**WEOF**します。 **Getc**を使用して、 **ferror**または**feof**エラーまたはファイルの終わりを確認します。 場合*ストリーム*は**NULL**、 **getc**と**getwc** 」の説明に従って、無効なパラメーター ハンドラーを呼び出す[パラメーター検証](../../c-runtime-library/parameter-validation.md)です。 これらの関数を返すかどうかは、引き続き実行が許可された、 **EOF** (または**WEOF**の**getwc**) を設定および**errno**に**EINVAL**します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

各ルーチンはファイルの現在の位置から 1 文字読み取り、関連付けられたファイル ポインター (定義されている場合) をインクリメントして次の文字を指します。 ファイルが関連付けられている*ストリーム*します。

これらの関数は呼び出し元スレッドをロックするため、スレッド セーフです。 ロックしないバージョンについては、「[_getc_nolock、_getwc_nolock](getc-nolock-getwc-nolock.md)」をご覧ください。

ルーチン固有の解説は、次のとおりです。

|ルーチンによって返される値|Remarks|
|-------------|-------------|
|**getc**|同じ**fgetc**が、関数およびマクロとして実装されています。|
|**getwc**|ワイド文字バージョン**getc**します。 マルチバイト文字またはワイド文字かどうかに従って読み取り*ストリーム*はテキスト モードとバイナリ モードで開かれます。|

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc**|**getc**|**getwc**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crtgetctxt"></a>入力: crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>出力

```Output
Input was: Line one.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
[ungetc、ungetwc](ungetc-ungetwc.md)<br/>
