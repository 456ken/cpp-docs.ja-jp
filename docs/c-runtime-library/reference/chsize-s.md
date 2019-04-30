---
title: _chsize_s
ms.date: 11/04/2016
apiname:
- _chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: a56efe826d43c80dc2cdee295e58872e7dd3c9ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348511"
---
# <a name="chsizes"></a>_chsize_s

ファイル サイズを変更します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_chsize](chsize.md) です。

## <a name="syntax"></a>構文

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルを参照するファイル記述子。

*size*<br/>
バイト単位のファイルの新しい長さ。

## <a name="return-value"></a>戻り値

**_chsize_s**ファイル サイズが正常に変更された場合、値 0 を返します。 0 以外の戻り値は、エラーを示します戻り値は**EACCES**アクセスに対して、指定したファイルがロックされている場合**EBADF**場合、指定したファイルが読み取り専用または記述子が有効でない場合 **。ENOSPC** 、デバイス上の領域が残っていない場合または**EINVAL**サイズが 0 よりも小さい場合。 **errno**が同じ値に設定します。

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Chsize_s**関数の拡張またはに関連付けられているファイルを切り捨てます*fd*で指定された長さに*サイズ*します。 ファイルは、書き込みを許可するモードで開かれている必要があります。 ファイルが拡張される場合は、null 文字 ('\0') が追加されます。 ファイルが切り捨てられる場合、短くなったファイルの末尾からファイルの元の長さまでのすべてのデータは失われます。

**_chsize_s**ファイル サイズとして 64 ビット整数を受け取り、4 GB を超えるファイル サイズを処理できます。 **_chsize**は 32 ビット ファイルのサイズに制限されます。

この関数は、パラメーターを検証します。 場合*fd*は無効なパラメーター ハンドラーが呼び出される、有効なファイル記述子またはサイズが 0 より小さい」の説明に従って[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
