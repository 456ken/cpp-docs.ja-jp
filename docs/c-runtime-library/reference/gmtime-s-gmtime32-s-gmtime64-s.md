---
title: gmtime_s、_gmtime32_s、_gmtime64_s
ms.date: 11/04/2016
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: 8225fed21ca9dc67440a4af5dcf43b2ad5cfdffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157449"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s、_gmtime32_s、_gmtime64_s

時刻値に変換する**tm**構造体。 これらは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」 (CRT のセキュリティ機能) で説明されているように、セキュリティが強化されたバージョンの [_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md) です。

## <a name="syntax"></a>構文

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>パラメーター

*tmDest*<br/>
ポインターを[tm](../../c-runtime-library/standard-types.md)構造体。 返される構造体のフィールドの評価値を保持する、*タイマー*現地時刻ではなく UTC での引数。

*sourceTime*<br/>
格納されている時刻へのポインター。 時刻は、世界協定時刻 (UTC: Coordinated Universal Time) の 1970 年 1 月 1 日の深夜 00:00:00 から経過した時間 (秒単位) を表します。

## <a name="return-value"></a>戻り値

正常終了した場合は 0。 障害が発生した場合、戻り値はエラー コードを示します。 エラー コードは Errno.h で定義されます。これらのエラーの一覧については、[errno](../../c-runtime-library/errno-constants.md) をご覧ください。

### <a name="error-conditions"></a>エラー条件

|*tmDest*|*sourceTime*|Return|値*tmDest*|
|-----------|------------|------------|--------------------|
|**NULL**|任意|**EINVAL**|変更されません。|
|いない**NULL** (有効なメモリを指す)|**NULL**|**EINVAL**|すべてのフィールドが-1 に設定されます。|
|いない**NULL**|< 0|**EINVAL**|すべてのフィールドが-1 に設定されます。|

最初の 2 つのエラーの場合は、「[Parameter Validation](../../c-runtime-library/parameter-validation.md)」 (パラメーターの検証) に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合に、これらの関数が設定**errno**に**EINVAL**戻って**EINVAL**します。

## <a name="remarks"></a>Remarks

**_Gmtime32_s**関数、 *sourceTime*値し、型の構造体に格納**tm**Time.h に定義します。 構造体のアドレスが渡された*tmDest*します。 値*sourceTime*への呼び出しは通常、[時間](time-time32-time64.md)関数。

> [!NOTE]
> 対象の環境によって、夏時間が有効かどうか判断されます。 C ランタイム ライブラリでは、アメリカ合衆国の規則を前提に夏時間を計算します。

型の構造体のフィールドの各は**int**、次の表に示すようにします。

|フィールド|説明|
|-|-|
|**tm_sec**|秒 (0 - 59)。|
|**tm_min**|分 (0 - 59)。|
|**tm_hour**|午前 0 時からの経過時間 (0 - 23)。|
|**tm_mday**|(1 ~ 31) の月の日。|
|**tm_mon**|月 (0 - 11年 1 月 = 0 です)。|
|**tm_year**|年 (実際の西暦から 1900 を引いた数)|
|**tm_wday**|週の曜日 (0 ~ 6 です。日曜日 = 0)。|
|**tm_yday**|年の通算日 (0 - 365;1 月 1 日 = 0)。|
|**tm_isdst**|常に 0 の**gmtime_s**します。|

**_gmtime64_s**、使用、 **_ _time64_t**構造体、ことができますを UTC; 3000 年 12 月 31 日 23時 59分: 59 秒を表す日付**gmtime32_s**しかまでの日付を表す23時 59分: 59、2038 年 1 月 18 日 UTC。 これらの関数の日付範囲の下限は、どちらも 1970 年 1 月 1 日の午前 0 時です。

**gmtime_s**に評価されるインライン関数は、 **_gmtime64_s**と**time_t**と等価 **_ _time64_t**します。 強制的にコンパイラを解釈する必要がある場合**time_t**古い 32 ビットとして**time_t**を定義できます **_USE_32BIT_TIME_T**します。 これにより**gmtime_s**をインラインにする **_gmtime32_s**します。 ただし、この方法は推奨されません。2038 年 1 月 18 日以降にアプリケーションがエラーになる可能性があり、また、64 ビット プラットフォームでは使用できないためです。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須の C ヘッダー|必須の C++ ヘッダー|
|-------------|---------------------|-|
|**gmtime_s**、 **_gmtime32_s**、 **_gmtime64_s**|\<time.h>|\<ctime > または\<time.h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
