---
title: mbsrtowcs_s
ms.date: 11/04/2016
apiname:
- mbsrtowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: a935b5181078f3b08ba5f2f89c581ed8cce8ded5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156669"
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

現在のロケールのマルチバイト文字の文字列をワイド文字の文字列表現に変換します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおりセキュリティーが強化されたバージョンの [mbsrtowcs](mbsrtowcs.md) です。

## <a name="syntax"></a>構文

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>パラメーター

*pReturnValue*<br/>
変換された文字数。

*wcstr*<br/>
結果として変換されたワイド文字の文字列を格納するバッファーのアドレス。

*sizeInWords*<br/>
サイズ*wcstr*単語 (ワイド文字)。

*mbstr*<br/>
変換されるマルチバイト文字の文字列の場所への間接ポインター。

*count*<br/>
格納するワイド文字の最大数、 *wcstr*バッファー、終端の null は含まないまたは[_TRUNCATE](../../c-runtime-library/truncate.md)します。

*mbstate*<br/>
ポインター、 **mbstate_t**変換状態オブジェクト。 この値が null ポインターの場合、静的な内部変換状態オブジェクトが使用されます。 内部**mbstate_t**オブジェクトはスレッド セーフではありませんを常に渡す独自ことをお勧めします。*呼び出すため*パラメーター。

## <a name="return-value"></a>戻り値

変換が正常に終了した場合は 0 を返し、失敗した場合はエラー コードを返します。

|エラー条件|戻り値および**errno**|
|---------------------|------------------------------|
|*wcstr* null ポインターと*sizeInWords* > 0|**EINVAL**|
|*mbstr* null ポインター|**EINVAL**|
|文字列直接に指す*mbstr*現在のロケールの無効なマルチバイト シーケンスが含まれています。|**EILSEQ**|
|コピー先のバッファーが小さすぎて変換後の文字列を含む (しない限り、*カウント*は **_TRUNCATE**; 詳細については、「解説」を参照してください)|**ERANGE**|

これらのいずれかの条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているとおり無効なパラメーター例外が呼び出されます。 実行の継続が許可された場合、関数はエラー コードを返します設定と**errno**表に記載されています。

## <a name="remarks"></a>Remarks

**Mbsrtowcs_s**関数が直接に指すマルチバイト文字の文字列に変換します*mbstr*が指すバッファーに格納されているワイド文字に*wcstr*により、含まれる変換状態を使用して*呼び出すため*します。 これらの条件のいずれかが満たされるまで、各文字に対して変換が続きます。

- マルチバイトの null 文字が検出されました。

- 無効なマルチバイト文字が検出されました。

- 格納されるワイド文字の数、 *wcstr* equals をバッファー*カウント*します。

コピー先文字列*wcstr*は常にエラー発生時でも、null で終わる場合を除き、 *wcstr* null ポインターです。

場合*カウント*特殊な値は、 [_TRUNCATE](../../c-runtime-library/truncate.md)、 **mbsrtowcs_s**コピー先のバッファーは null の空きを残して収まる限りの文字列の多くに変換されますターミネータ。

場合**mbsrtowcs_s** 、元の文字列を正常に変換の変換後の文字列とに終端の null ワイド文字のサイズが置かれる *&#42;pReturnValue*に用意されている*pReturnValue* null ポインターではありません。 これが発生した場合でも、 *wcstr*引数が null ポインターであり、必要なバッファー サイズを決定することができます。 その場合に注意してください*wcstr* null ポインターの場合は、*カウント*は無視されます。

場合*wcstr*が null ポインターを指すポインター オブジェクト*mbstr*終端の null 文字に達したために、変換が停止している場合に null ポインターが割り当てられます。 それ以外の場合、変換された最後のマルチバイト文字がある場合は、その後ろのアドレスが割り当てられます。 これにより、後続の関数呼び出しで、この呼び出しが停止した場所から変換を再開できます。

場合*呼び出すため*が null ポインターの場合、ライブラリの内部**mbstate_t**変換状態の静的オブジェクトを使用します。 渡す独自ことをお勧めこの内部静的オブジェクトはスレッド セーフではないため、*呼び出すため*値。

場合**mbsrtowcs_s**マルチバイト文字の現在のロケールが無効ですが検出されたに-1 を入れ *&#42;pReturnValue*、コピー先のバッファーを設定*wcstr*空の文字列に次のように設定します。 **errno**に**EILSEQ**、し、返します**EILSEQ**します。

によって、シーケンスを指している場合*mbstr*と*wcstr*の動作が重なる**mbsrtowcs_s**が定義されていません。 **mbsrtowcs_s**は現在のロケールの LC_TYPE カテゴリを受けます。

> [!IMPORTANT]
> いることを確認*wcstr*と*mbstr*重複しないと*数*変換するマルチバイト文字の数を正確に反映します。

**Mbsrtowcs_s**関数とは異なります[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)によってその再起動します。 変換の状態が格納されている*呼び出すため*同じか、またはその他の再開可能な関数を呼び出すのためです。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。 たとえば、アプリケーションで使用する**mbsrlen**の代わりに**mbslen**後続の呼び出しの場合は、 **mbsrtowcs_s**の代わりに使用が**mbstowcs_s**.

C++ では、この関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="exceptions"></a>例外

**Mbsrtowcs_s**場合、現在のスレッドの呼び出しでない関数、関数はマルチ スレッド セーフ**setlocale**この関数を実行している限り、*呼び出すため*引数は、null ポインターではありません。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
