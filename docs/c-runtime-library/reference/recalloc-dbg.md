---
title: _recalloc_dbg
ms.date: 11/04/2016
apiname:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: e2782492d3338b5b548db0153b6123fb82ff5e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357689"
---
# <a name="recallocdbg"></a>_recalloc_dbg

配列を再割り当てし、その要素を 0 に初期化します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*userData*<br/>
以前に割り当てられていたメモリ ブロックへのポインター。

*number*<br/>
要求するメモリ ブロックの数。

*size*<br/>
要求する各メモリ ブロックのサイズ (バイト)。

*blockType*<br/>
要求されたメモリ ブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**します。

割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

*ファイル名*<br/>
割り当て操作を要求したソース ファイルの名前へのポインターまたは**NULL**します。

*行番号*<br/>
割り当て操作が要求されたソース ファイル内の番号を行または**NULL**します。

*Filename*と*linenumber*ときにパラメーターが使用可能なだけ **_recalloc_dbg**が明示的に呼び出された、または[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)プリプロセッサ定数が定義されています。

## <a name="return-value"></a>戻り値

正常に完了する、この関数は再割り当てされたメモリ ブロックのユーザー部分へのポインターを返します、新しいハンドラー関数を呼び出すか、返すか**NULL**します。 戻る動作の詳細については、後の「解説」のセクションを参照してください。 新しいハンドラー関数がどのように使用されるかの詳細については、[_recalloc](recalloc.md) 関数を参照してください。

## <a name="remarks"></a>Remarks

**_recalloc_dbg**のデバッグ バージョンです、 [_recalloc](recalloc.md)関数。 ときに[_DEBUG](../../c-runtime-library/debug.md)が定義されていない呼び出しごとに **_recalloc_dbg**への呼び出しに減少 **_recalloc**します。 両方 **_recalloc**と **_recalloc_dbg**ベースのヒープにメモリ ブロックを再割り当てが **_recalloc_dbg**はいくつかのデバッグ機能を提供しますいずれかの側のバッファー。リークをテストする、ブロックのユーザー部分のブロックが特定の割り当ての種類を追跡するためにパラメーターを入力し、 *filename*/*linenumber*を特定する情報、割り当て要求の起点。

**_recalloc_dbg** 、要求されたサイズよりも少し多い領域を指定されたメモリ ブロックを再割り当て (*数* * *サイズ*) のサイズよりも小さいか大きい可能性があります最初に割り当てられたメモリ ブロックです。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 再割り当てによって、元のメモリ ブロックがヒープ内の別の位置に移動されたり、メモリ ブロックのサイズが変わったりする場合があります。 ブロックのユーザー部分には値 0xCD が設定され、各上書きバッファーには 0xFD が設定されます。

**_recalloc_dbg**設定**errno**に**ENOMEM**メモリ割り当てが失敗した場合。**EINVAL** (以前に説明したオーバーヘッドを含む) に必要なメモリの量を超えたかどうかに返される **_HEAP_MAXREQ**します。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
