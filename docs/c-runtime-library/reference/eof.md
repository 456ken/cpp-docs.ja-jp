---
title: _eof
ms.date: 11/04/2016
apiname:
- _eof
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
- _eof
helpviewer_keywords:
- eof function
- end of file, testing for
- _eof function
- files [C++], end of
- testing, for end-of-file
- end of file
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
ms.openlocfilehash: 1da849c3721d4d83ff0b3166bc18f95728ebf124
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288137"
---
# <a name="eof"></a>_eof

ファイルの終わり (EOF) かどうかをテストします。

## <a name="syntax"></a>構文

```C
int _eof(
   int fd
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルを参照するファイル記述子。

## <a name="return-value"></a>戻り値

**_eof**でない場合、現在の位置がファイルの最後または 0 の場合は 1 を返します。 戻り値-1 はエラーを示します無効なパラメーター ハンドラーが呼び出されるこの場合、」の説明に従って[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 続けるには、実行が許可された場合**errno**に設定されている**EBADF**、無効なファイル記述子を示します。

## <a name="remarks"></a>Remarks

**_Eof**関数は、ファイルの末尾に関連付けられているかどうかを決定します。 *fd*に達しています。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|オプション ヘッダー|
|--------------|---------------------|---------------------|
|**_eof**|\<io.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_eof.c
// This program reads data from a file
// ten bytes at a time until the end of the
// file is reached or an error is encountered.
//
#include <io.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   int  fh, count, total = 0;
   char buf[10];
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
        perror( "Open failed");
        exit( 1 );
   }
   // Cycle until end of file reached:
   while( !_eof( fh ) )
   {
      // Attempt to read in 10 bytes:
      if( (count = _read( fh, buf, 10 )) == -1 )
      {
         perror( "Read error" );
         break;
      }
      // Total actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   _close( fh );
}
```

### <a name="input-crteoftxt"></a>入力: crt_eof.txt

```Input
This file contains some text.
```

### <a name="output"></a>出力

```Output
Number of bytes read = 29
```

## <a name="see-also"></a>関連項目

[エラー処理](../../c-runtime-library/error-handling-crt.md)<br/>
[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
