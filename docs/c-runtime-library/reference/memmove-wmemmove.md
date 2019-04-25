---
title: memmove、wmemmove
ms.date: 11/04/2016
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 988af1c2678e20ea40ce4dfe331a3b6c49db0547
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156565"
---
# <a name="memmove-wmemmove"></a>memmove、wmemmove

バッファーを別のバッファーに移動します。 これらの関数にはセキュリティを強化したバージョンがあります。「[memmove_s、wmemmove_s](memmove-s-wmemmove-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>パラメーター

*dest*<br/>
コピー先のオブジェクト。

*src*<br/>
コピー元のオブジェクト。

*count*<br/>
バイト数 (**memmove**) または文字 (**wmemmove**) にコピーします。

## <a name="return-value"></a>戻り値

値*dest*します。

## <a name="remarks"></a>Remarks

コピー*カウント*バイト (**memmove**) または文字 (**wmemmove**) から*src*に*dest*します。 コピー元とコピー先の領域の一部が重なり合っている場合、どちらの関数も、重なり合っている領域のコピー元のバイトをコピーした後で上書きします。

**セキュリティに関するメモ** コピー先のバッファーのサイズがソース バッファー以上であることをご確認ください。 詳しくは、「 [バッファー オーバーランの回避](/windows/desktop/SecBP/avoiding-buffer-overruns)」をご覧ください。

**Memmove**と**wmemmove**場合、関数は廃止のみ定数 **_CRT_SECURE_DEPRECATE_MEMORY**の順序でインクルード ステートメントの前に定義されます次の例に示すように、非推奨にする関数。

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

または

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>関連項目

[バッファー操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
