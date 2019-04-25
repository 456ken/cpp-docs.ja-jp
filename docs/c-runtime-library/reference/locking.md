---
title: _locking
ms.date: 11/04/2016
apiname:
- _locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 90327ed3388d4f18e0f64f92c33112c9ddd800f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157464"
---
# <a name="locking"></a>_locking

ファイルのバイトをロックまたはロック解除します。

## <a name="syntax"></a>構文

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
ファイル記述子。

*モード*<br/>
実行するロック アクション。

*nbytes*<br/>
ロックするバイト数。

## <a name="return-value"></a>戻り値

**_locking**成功した場合は 0 を返します。 戻り値-1 はエラーを示します後者[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)値は次のいずれかに設定されます。

|errno の値|条件|
|-|-|
| **EACCES** | ロック違反 (ファイルはすでにロックされている場合もロック解除されている場合もある)。 |
| **EBADF** | 無効なファイル記述子。 |
| **EDEADLOCK** | ロック違反。 ときに返される、 **_LK_LOCK**または **_LK_RLCK**フラグが指定されており、10 回試行した後、ファイルをロックできません。 |
| **EINVAL** | 無効な引数が指定された **_locking**します。 |

エラーの原因が無効なファイル記述子などの無効なパラメーターである場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。

## <a name="remarks"></a>Remarks

**_Locking**関数は、ロックまたはロック解除*nbytes*バイトで指定されたファイルの*fd*します。 ファイル内のバイトをロックすると、他のプロセスがそれらのバイトにアクセスできなくなります。 すべてのロックまたはロック解除は、ファイル ポインターの現在の位置から開始され、次の *nbytes* バイトに進みます。 ファイルの終わりを超えてバイトをロックできます。

*mode* は、Locking.h で定義されている、次のマニフェスト定数のいずれかである必要があります。

|*モード*値|効果|
|-|-|
| **_LK_LOCK** | 指定したバイトをロックします。 バイトをロックできない場合、プログラムによって 1 秒後に直ちに再試行されます。 10 回試行した後、バイトをロックできなかった場合、定数はエラーを返します。 |
| **_LK_NBLCK** | 指定したバイトをロックします。 バイトをロックできない場合、定数はエラーを返します。 |
| **_LK_NBRLCK** | 同じ **_LK_NBLCK**します。 |
| **_LK_RLCK** | 同じ **_LK_LOCK**します。 |
| **_LK_UNLCK** | 指定したバイトのロックを解除します。バイトは既にロックされている必要があります。 |

重複しない、ファイルの複数の領域をロックできます。 ロック解除の対象領域は、既にロックされている必要があります。 **_locking**隣接する領域をマージしないのは、2 つのロックされた領域が隣接している場合は、各リージョンする必要がありますロックを解除するとは別にします。 領域は短期間だけロックされ、ファイルを閉じる前またはプログラムを終了する前にはロックを解除する必要があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h> と \<sys/locking.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crtlockingtxt"></a>入力: crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>出力例

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
