---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_malloc_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: eb58313c892ffe13e9f8e34e98b7940022899d14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341640"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

デバッグ ヘッダーと上書きバッファー用の追加の領域を持つメモリを、指定された配置境界に割り当てます (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
要求されたメモリ割り当てのサイズ。

*alignment*<br/>
アラインメント値。2 の整数乗である必要があります。

*ファイル名*<br/>
割り当て操作を要求したソース ファイル名へのポインターまたは NULL。

*行番号*<br/>
割り当て操作が要求されたソース ファイル内の行番号または NULL。

## <a name="return-value"></a>戻り値

割り当てられたメモリ ブロックへのポインターまたは NULL の場合は、操作に失敗しました。

## <a name="remarks"></a>Remarks

**_aligned_malloc_dbg**のデバッグ バージョンです、 [_aligned_malloc](aligned-malloc.md)関数。 ときに[_DEBUG](../../c-runtime-library/debug.md)が定義されていない呼び出しごとに **_aligned_malloc_dbg**への呼び出しに減少`_aligned_malloc`します。 両方`_aligned_malloc`と **_aligned_malloc_dbg**ベースのヒープのメモリのブロックを割り当てますが、 **_aligned_malloc_dbg**いくつかのデバッグ機能を提供しています: のユーザー部分の両側のバッファー、リークをテストするブロックと*filename*/*linenumber*割り当て要求の起点を特定する情報。 ブロックの型パラメーターを持つ特定の割り当ての種類の追跡は、アラインされた割り当てのサポートされているデバッグ機能ではありません。 アラインされた割り当ては、_NORMAL_BLOCK ブロックの型として表示されます。

**_aligned_malloc_dbg**メモリ ブロックを要求したよりも少し多い領域を割り当てます*サイズ*します。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 ブロックが割り当てられると、ブロックのユーザー部分には値 0xCD が設定され、各上書きバッファーには 0xFD が設定されます。

**_aligned_malloc_dbg**設定`errno`に`ENOMEM`メモリ割り当てが失敗した場合、または (以前に説明したオーバーヘッドを含む) に必要なメモリの量を超えた場合`_HEAP_MAXREQ`します。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。 また、 **_aligned_malloc_dbg**パラメーターを検証します。 場合*配置*が 2 の累乗でないまたは*サイズ*ゼロ、」の説明に従って、この関数は、無効なパラメーター ハンドラーを呼び出します[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 実行が続行すると、この関数は NULL を返し、セットを許可された場合`errno`に`EINVAL`します。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)