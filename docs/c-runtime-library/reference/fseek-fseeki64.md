---
title: fseek、_fseeki64
ms.date: 11/04/2016
apiname:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e5f775eab370f8f4a3b6a5c1d7f0918ec7efa3ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287587"
---
# <a name="fseek-fseeki64"></a>fseek、_fseeki64

指定した場所にファイル ポインターを移動します。

## <a name="syntax"></a>構文

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>パラメーター

*stream*<br/>
**FILE** 構造体へのポインター。

*オフセット*<br/>
*配信元*からのバイト数。

*配信元*<br/>
最初の位置。

## <a name="return-value"></a>戻り値

成功した場合、 **fseek**と **_fseeki64** 0 を返します。 それ以外の場合は、0 以外の値を返します。 シーク非対応のデバイスでは、戻り値は未定義です。 場合*ストリーム*null ポインターの場合は、場合*原点*が許可されている値を以下に示すいずれかの**fseek**と **_fseeki64**無効なを呼び出すパラメーターのハンドラーを」の説明に従って[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 実行の継続が許可された場合に、これらの関数が設定**errno**に**EINVAL**し、-1 を返します。

## <a name="remarks"></a>Remarks

**Fseek**と **_fseeki64**関数ファイル ポインター (存在する場合) に関連付けられている移動*ストリーム*である新しい場所に*オフセット*バイト*原点*します。 ストリームの次の操作は、新しい場所で行われます。 更新用に開かれているストリームでの次の操作は読み取りまたは書き込みのいずれかです。 引数*原点*STDIO で定義されている、次の定数のいずれかを指定する必要があります。H:

|配信元の値|説明|
|-|-|
| **SEEK_CUR** | ファイル ポインターの現在の位置。 |
| **オフセット** | EOF (ファイル終端)。 |
| **SEEK_SET** | ファイルの先頭。 |

使用することができます**fseek**と **_fseeki64**ファイル内の任意の場所にポインターを移動します。 ポインターは、ファイルの末尾を越えて配置することもできます。 **fseek**と **_fseeki64** 、ファイルの終わりインジケーターをクリアし、前のすべての効果が無視されます[ungetc](ungetc-ungetwc.md)に対する*ストリーム*します。

データを追加するためにファイルを開く場合、現在のファイルの位置は、次の書き込みが発生する場所ではなく最後の I/O 操作によって決まります。 追加のために開かれたファイルで I/O 操作がまだ発生していない場合、ファイルの位置はファイルの先頭です。

テキスト モードで開かれたストリームの**fseek**と **_fseeki64**キャリッジ リターンとラインフィードの変換が発生することができますので、用途が限定**fseek**と **_fseeki64**予期しない結果を生成します。 唯一**fseek**と **_fseeki64**テキスト モードで開かれたストリームで動作する保証の操作します。

- 元の値のいずれかに対して相対的なオフセット 0 でシークします。

- 呼び出しから返されるオフセット値を使用して、ファイルの先頭からシーク[ftell](ftell-ftelli64.md)を使用する場合**fseek**または[_ftelli64](ftell-ftelli64.md)を使用する場合 **_fseeki64**.

テキスト モードでも、Ctrl + Z は入力時に EOF (EOF: end-of-file) 文字として解釈されます。 ファイルを読み取り/書き込み、開いた[fopen](fopen-wfopen.md)と関連するすべてのルーチンは、ファイルの末尾に CTRL + Z 確認し、可能であれば削除します。 これはの組み合わせを使用して、 **fseek**と[ftell](ftell-ftelli64.md)または **_fseeki64**と[_ftelli64](ftell-ftelli64.md)で終わるファイル内で移動するには、CTRL + Z が生じる**fseek**または **_fseeki64**ファイルの末尾近くが正しく動作しません。

バイト オーダー マーク (BOM) で始まるファイルを CRT で開くときには、ファイル ポインターは BOM の後ろ (つまり、ファイルの実際のコンテンツの開始位置) に配置されます。 しなければならない場合**fseek**ファイルの先頭を使用して[ftell](ftell-ftelli64.md)初期位置を取得して**fseek** 0 の位置ではなく、それにします。

この関数では、実行中に他のスレッドをロックするので、スレッド セーフです。 ロックしないバージョンについては、「[_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
