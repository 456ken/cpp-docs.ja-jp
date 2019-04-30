---
title: clearerr
ms.date: 11/04/2016
apiname:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: c282a577bb7496f899f18abeac857c08388d12f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340562"
---
# <a name="clearerr"></a>clearerr

ストリームのエラー インジケーターをリセットします。 この関数のセキュリティが強化されたバージョンについては、「[clearerr_s](clearerr-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*stream*<br/>
**FILE** 構造体へのポインター。

## <a name="remarks"></a>Remarks

**Clearerr**関数は、エラー インジケーターとファイルの終わりインジケーターをリセット*ストリーム*します。 エラー インジケーターは自動的にクリアされません。そのストリームに対する操作が引き続きまでエラー値を返し、指定したストリームのエラー インジケーターを設定すると、 **clearerr**、 [fseek](fseek-fseeki64.md)、 **fsetpos**、または[巻き戻し](rewind.md)が呼び出されます。

場合*ストリーム*は**NULL**で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 実行の継続が許可された場合に、この関数が設定**errno**に**EINVAL**を返します。 詳細については**errno** 、エラー コードを参照してくださいと[errno 定数](../../c-runtime-library/errno-constants.md)します。

この関数のセキュリティが強化されたバージョンについては、「[clearerr_s](clearerr-s.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>入力

```Input
n
```

### <a name="output"></a>出力

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>関連項目

[エラー処理](../../c-runtime-library/error-handling-crt.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
