---
title: bsearch_s
ms.date: 11/04/2016
apiname:
- bsearch_s
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
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: 56c5fa45a9d8f9ac9b22474601934d3994da55e4
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210953"
---
# <a name="bsearchs"></a>bsearch_s

並べ替えられた配列のバイナリ検索を実行します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [bsearch](bsearch.md) です。

## <a name="syntax"></a>構文

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
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
2 つの要素を比較するコールバック関数。 最初の引数は、*コンテキスト*ポインター。 2 番目の引数がへのポインター、*キー*検索します。 3 番目の引数と比較する配列要素へのポインターは、*キー*します。

*context*<br/>
比較関数内でアクセスできるオブジェクトへのポインター。

## <a name="return-value"></a>戻り値

**bsearch_s**の発生個所へのポインターを返します*キー*が指す配列で*基本*します。 場合*キー*が見つからない、関数を返します**NULL**します。 配列が昇順でないか、同一キーで重複するレコードがある場合、結果は予測不可能になります。

この関数に無効なパラメーターが渡されると、「 [Parameter Validation](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター ハンドラーが呼び出されます。 続けるには、実行が許可された場合**errno**に設定されている**EINVAL** 、関数を返します**NULL**します。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

### <a name="error-conditions"></a>エラー条件

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*compare*|*number*|*width*|**errno**|
|**NULL**|任意|任意|任意|任意|**EINVAL**|
|任意|**NULL**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|= 0|**EINVAL**|
|任意|任意|**NULL**|1 つ|任意|**EINVAL**|

## <a name="remarks"></a>Remarks

**Bsearch_s**関数の並べ替え済み配列のバイナリ検索を実行する*数*の各要素は、*幅*サイズ (バイト)。 *基本*値は、検索対象の配列のベースへのポインターと*キー*検索されている値です。 *比較*パラメーターを配列要素への要求されたキーを比較し、それらの関係を指定する値は次のいずれかを返しますユーザー指定のルーチンへのポインターです。

|によって返される値*比較*ルーチン|説明|
|-----------------------------------------|-----------------|
|\< 0|キーは配列要素より小さい。|
|0|キーは配列要素と等しい。|
|> 0|キーは配列要素より大きい。|

*コンテキスト*検索対象のデータ構造体は、オブジェクトの一部との比較関数は、オブジェクトのメンバーにアクセスする必要がある場合、ポインターが便利な可能性があります。 *比較*関数はそのオブジェクトの適切なオブジェクトの種類とアクセスのメンバーに void ポインターをキャストすることがあります。 追加、*コンテキスト*パラメーターにより、 **bsearch_s**追加のコンテキストに関連付けられたデータを使用できるようにする静的変数を使用して、再入バグを回避するのに使用できるためより安全な*比較*関数。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> および \<search.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムでは、 [qsort_s](qsort-s.md)で文字列の配列を並べ替え、bsearch_s を使用して "cat" という単語を検索します。

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
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
