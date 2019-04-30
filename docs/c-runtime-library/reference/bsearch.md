---
title: bsearch
ms.date: 11/04/2016
apiname:
- bsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: e170ce67d22c0d97825a7eb754546a29daac6d89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347757"
---
# <a name="bsearch"></a>bsearch

並べ替えられた配列のバイナリ検索を実行します。 この関数のセキュリティが強化されたバージョンについては、「[bsearch_s](bsearch-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索するオブジェクト。

*base*<br/>
検索データのベースへのポインター。

*number*<br/>
要素の数。

*width*<br/>
要素の幅。

*compare*<br/>
2 つの要素を比較するコールバック関数。 最初のものは検索対象のキーへのポインターで、2 番目はキーと比較する配列要素へのポインターです。

## <a name="return-value"></a>戻り値

**bsearch**の発生個所へのポインターを返します*キー*が指す配列で*基本*します。 場合*キー*が見つからない、関数を返します**NULL**します。 配列が昇順でないか、同一キーで重複するレコードがある場合、結果は予測不可能になります。

## <a name="remarks"></a>Remarks

**Bsearch**関数の並べ替え済み配列のバイナリ検索を実行する*数*の各要素は、*幅*サイズ (バイト)。 *基本*値は、検索対象の配列のベースへのポインターと*キー*検索されている値です。 *比較*パラメーターを配列要素への要求されたキーを比較し、それらの関係を指定する値は次のいずれかを返しますユーザー指定のルーチンへのポインターです。

|によって返される値*比較*ルーチン|説明|
|-----------------------------------------|-----------------|
|\< 0|キーは配列要素より小さい。|
|0|キーは配列要素と等しい。|
|> 0|キーは配列要素より大きい。|

この関数は、パラメーターを検証します。 場合*比較*、*キー*または*数*は**NULL**、または*基本*は**NULL**と*数*0 以外の場合、または*幅*0 の場合で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 続けるには、実行が許可された場合**errno**に設定されている`EINVAL`、関数を返します**NULL**します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> および \<search.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムでは、qsort で文字列の配列を並べ替え、bsearch を使用して "cat" という単語を検索します。

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
