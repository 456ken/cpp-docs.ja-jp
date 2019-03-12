---
title: _outp、_outpw、_outpd
ms.date: 11/04/2016
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 1a507f4115a48372706590eb61f9e3e77a0e3548
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752065"
---
# <a name="outp-outpw-outpd"></a>_outp、_outpw、_outpd

1 バイト (`_outp`)、1 ワード (`_outpw`)、または 1 ダブルワード (`_outpd`) のいずれかをポートに出力します。

> [!IMPORTANT]
>  これらは古い関数です。 Visual Studio 2015 以降では、CRT で使用できません。

> [!IMPORTANT]
>  この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```

      int _outp(
unsigned short port,
int databyte
);
unsigned short _outpw(
unsigned short port,
unsigned short dataword
);
unsigned long _outpd(
unsigned short port,
unsigned long dataword
);
```

#### <a name="parameters"></a>パラメーター
*port*<br/>
ポート番号。

*databyte、dataword*<br/>
出力値。

## <a name="return-value"></a>戻り値

関数は、出力データを返します。 エラーの戻り値はありません。

## <a name="remarks"></a>解説

`_outp`、 `_outpw`、 `_outpd` の各関数は、指定された出力ポートへそれぞれバイト、ワード、ダブルワードを 1 つ書き込みます。 *port* 引数は、0 - 65,535 の任意の符号なし整数です。 *databyte* は、0 - 255 の任意の整数です。*dataword* は、整数、符号なし短整数、および符号なし長整数の範囲の任意の値です。

これらの関数は I/O ポートへ直接書き込まれるため、ユーザー コードで使用できません。 これらのオペレーティング システムでの I/O ポートの使用方法については、MSDN で「Serial Communications in Win32 (Win32 のシリアル通信)」を検索してください。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

互換性の詳細については、「 [互換性](../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)
