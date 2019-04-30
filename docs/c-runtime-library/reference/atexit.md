---
title: atexit
ms.date: 11/04/2016
apiname:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: 48f0fbfa1f3350f73899fcdbb3bf7922f1c6174d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341588"
---
# <a name="atexit"></a>atexit

終了時に指定された関数を処理します。

## <a name="syntax"></a>構文

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>パラメーター

*func*<br/>
呼び出される関数。

## <a name="return-value"></a>戻り値

**atexit**成功した場合、0、エラーが発生した場合は 0 以外の値を返します。

## <a name="remarks"></a>Remarks

**Atexit**関数には、関数のアドレスが渡されます*func*プログラムが正常に終了したときに呼び出されます。 連続して呼び出す**atexit** 、後入れ先出し (LIFO) の順序で実行される関数のレジスタが作成されます。 渡される関数は、 **atexit**パラメーターを受け取ることはできません。 **atexit**と **_onexit**関数のレジスタを保持するために、ヒープを使用します。 したがって、登録可能な関数の数は、ヒープ メモリの量によってのみ制限されます。

内のコード、 **atexit**関数は可能性がありますが既に読み込まれていない場合にある DLL への依存関係を含めることはできません、 **atexit**関数が呼び出されます。

ANSI 準拠のアプリケーションを生成するには、ANSI 標準を使用して**atexit**関数 (も同様ではなく **_onexit**関数)。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>例

このプログラムのプッシュ 4 つの関数のときに実行される関数のスタックに**atexit**が呼び出されます。 プログラムの終了時に、後入れ先出し法でこれらのプログラムが実行されます。

```C
// crt_atexit.c
#include <stdlib.h>
#include <stdio.h>

void fn1( void ), fn2( void ), fn3( void ), fn4( void );

int main( void )
{
   atexit( fn1 );
   atexit( fn2 );
   atexit( fn3 );
   atexit( fn4 );
   printf( "This is executed first.\n" );
}

void fn1()
{
   printf( "next.\n" );
}

void fn2()
{
   printf( "executed " );
}

void fn3()
{
   printf( "is " );
}

void fn4()
{
   printf( "This " );
}
```

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
