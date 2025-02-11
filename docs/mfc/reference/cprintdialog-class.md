---
title: CPrintDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: ccc673d665d6d5beb92f398b21e6ffd313a58fc9
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741360"
---
# <a name="cprintdialog-class"></a>CPrintDialog クラス

Windows のコモン ダイアログ ボックスである [印刷] ダイアログで提供されるサービスをカプセル化したものです。

## <a name="syntax"></a>構文

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|`CPrintDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|[印刷] ダイアログボックスを表示せずに、プリンターデバイスコンテキストを作成します。|
|[CPrintDialog::DoModal](#domodal)|ダイアログボックスを表示し、ユーザーが選択できるようにします。|
|[CPrintDialog::GetCopies](#getcopies)|要求されたコピーの数を取得します。|
|[CPrintDialog::GetDefaults](#getdefaults)|ダイアログボックスを表示せずに、デバイスの既定値を取得します。|
|[CPrintDialog::GetDeviceName](#getdevicename)|現在選択されているプリンターデバイスの名前を取得します。|
|[CPrintDialog::GetDevMode](#getdevmode)|`DEVMODE`構造体を取得します。|
|[CPrintDialog::GetDriverName](#getdrivername)|現在選択されているプリンタードライバーの名前を取得します。|
|[CPrintDialog::GetFromPage](#getfrompage)|印刷範囲の開始ページを取得します。|
|[CPrintDialog::GetPortName](#getportname)|現在選択されているプリンターポートの名前を取得します。|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|プリンターデバイスコンテキストへのハンドルを取得します。|
|[CPrintDialog::GetToPage](#gettopage)|印刷範囲の終了ページを取得します。|
|[CPrintDialog::PrintAll](#printall)|ドキュメントのすべてのページを印刷するかどうかを決定します。|
|[CPrintDialog::PrintCollate](#printcollate)|照合されたコピーが要求されるかどうかを決定します。|
|[CPrintDialog::PrintRange](#printrange)|指定した範囲のページだけを印刷するかどうかを決定します。|
|[CPrintDialog::P rintSelection](#printselection)|現在選択されている項目だけを印刷するかどうかを決定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|オブジェクトを`CPrintDialog`カスタマイズするために使用される構造体。|

## <a name="remarks"></a>Remarks

一般的な [印刷] ダイアログボックスを使用すると、Windows 標準と一貫性のある方法で印刷と印刷の設定のダイアログボックスを簡単に実装できます。

> [!NOTE]
>  クラス`CPrintDialogEx`は、Windows の [印刷] プロパティシートによって提供されるサービスをカプセル化します。 詳細については、「 [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)の概要」を参照してください。

`CPrintDialog`の機能は、 [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)の機能に置き換えられています。これは、印刷設定とページ設定の両方に共通のダイアログボックスを提供するように設計されています。

フレームワークに依存して、アプリケーションの印刷プロセスの多くの要素を処理できます。 この場合、フレームワークによって、印刷用の Windows コモンダイアログボックスが自動的に表示されます。 また、フレームワークでアプリケーションの印刷を処理することもできますが、[印刷] ダイアログボックスの [共通印刷] ダイアログボックスを使用した場合にはオーバーライドします。 フレームワークを使用して印刷タスクを処理する方法の詳細については、「[印刷](../../mfc/printing.md)」を参照してください。

アプリケーションで、フレームワークの関与なしに印刷を処理する場合は、提供され`CPrintDialog`たコンストラクターを使用して "そのまま" クラスを使用するか、から`CPrintDialog`独自のダイアログクラスを派生させ、必要に応じてコンストラクターを記述することができます。 どちらの場合も、これらのダイアログボックスはクラス`CCommonDialog`から派生しているので、標準の MFC ダイアログボックスのように動作します。

`CPrintDialog`オブジェクトを使用するには、最初に`CPrintDialog`コンストラクターを使用してオブジェクトを作成します。 ダイアログボックスが構築されたら、 [m_pd](#m_pd)構造体の任意の値を設定または変更して、ダイアログボックスのコントロールの値を初期化できます。 構造体の型は[PRINTDLG です。](/windows/win32/api/commdlg/ns-commdlg-printdlga) `m_pd` この構造の詳細については、Windows SDK を参照してください。

メンバー `m_pd` `hDevMode`と`GlobalFree`メンバーに対して独自のハンドルを指定しない場合は、ダイアログボックスが終了したときに、これらのハンドルに対して Windows の関数を呼び出す必要があります。 `hDevNames` に`CWinApp::OnFilePrintSetup`用意されているフレームワークの印刷設定の実装を使用する場合、これらのハンドルを解放する必要はありません。 ハンドルはによって`CWinApp`保持され、 `CWinApp`のデストラクターで解放されます。 スタンドアロンを使用`CPrintDialog`する場合にのみ、これらのハンドルを解放する必要があります。

ダイアログボックスコントロールを初期化した後、 `DoModal`メンバー関数を呼び出してダイアログボックスを表示し、ユーザーが印刷オプションを選択できるようにします。 `DoModal` ユーザーが [ok] \(IDOK) またはキャンセル (IDCANCEL) ボタンを選択するかどうかを返します。

が`DoModal` IDOK を返す場合は、のメンバー `CPrintDialog`関数のいずれかを使用して、ユーザーが入力した情報を取得できます。

この`CPrintDialog::GetDefaults`メンバー関数は、ダイアログボックスを表示せずに現在のプリンターの既定値を取得する場合に便利です。 このメンバー関数は、ユーザー操作を必要としません。

Windows `CommDlgExtendedError`の関数を使用すると、ダイアログボックスの初期化中にエラーが発生したかどうかを判断し、エラーの詳細を確認できます。 この関数の詳細については、Windows SDK を参照してください。

`CPrintDialog`は、COMMDLG に依存します。Windows バージョン3.1 以降に付属している DLL ファイル。

ダイアログボックスをカスタマイズするには、から`CPrintDialog`クラスを派生させ、カスタムダイアログテンプレートを指定して、拡張コントロールからの通知メッセージを処理するメッセージマップを追加します。 未処理のメッセージは、基本クラスに渡す必要があります。 フック関数のカスタマイズは必要ありません。

ダイアログボックスが印刷と印刷のどちらであるかによって、同じメッセージを異なる方法で処理するには、各ダイアログボックスのクラスを派生させる必要があります。 また、[印刷] ダイアログ`AttachOnSetup`ボックス内で [印刷設定] ボタンを選択した場合、新しいダイアログボックスの作成を処理する Windows 関数もオーバーライドする必要があります。

の使用方法`CPrintDialog`の詳細については、「[コモンダイアログクラス](../../mfc/common-dialog-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Windows 印刷または印刷設定のダイアログオブジェクトを構築します。

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*bPrintSetupOnly*<br/>
標準の Windows 印刷ダイアログボックスまたは印刷設定のダイアログボックスを表示するかどうかを指定します。 標準の Windows 印刷設定ダイアログボックスを表示するには、このパラメーターを TRUE に設定します。 Windows の [印刷] ダイアログボックスを表示するには、FALSE に設定します。 *Bprintsetuponly*が FALSE の場合でも、[印刷] ダイアログボックスに [印刷の設定] オプションボタンが表示されます。

*dwFlags*<br/>
ダイアログボックスの設定をカスタマイズするために使用できる1つ以上のフラグ。ビットごとの OR 演算子を使用して結合します。 たとえば、PD_ALLPAGES フラグは、既定の印刷範囲をドキュメントのすべてのページに設定します。 これらのフラグの詳細については、Windows SDK の[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)構造体を参照してください。

*pParentWnd*<br/>
ダイアログボックスの親またはオーナーウィンドウへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、オブジェクトを構築するだけです。 このダイアログ`DoModal`ボックスを表示するには、メンバー関数を使用します。

*Bprintsetuponly*を FALSE に設定してコンストラクターを呼び出すと、PD_RETURNDC フラグが自動的に使用されることに注意してください。 、 `DoModal` `m_pd.hDC`、または`GetPrinterDC`を呼び出すと、プリンターの DC がに返されます。 `GetDefaults` この DC は、の呼び出し元によって[DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)への`CPrintDialog`呼び出しを使用して解放する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)および[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)構造体からプリンターデバイスコンテキスト (DC) を作成します。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>戻り値

新しく作成されたプリンターデバイスコンテキストを処理します。

### <a name="remarks"></a>Remarks

この DC は、現在のプリンタ DC であると想定されています。また、以前に取得した他のすべてのプリンタ Dc は、ユーザーが削除する必要があります。 この関数は、[印刷] ダイアログボックスを表示せずに、結果として使用される DC を呼び出すことができます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>CPrintDialog::D oModal

[Windows コモン印刷] ダイアログボックスが表示されます。このダイアログボックスでは、印刷部数、ページ範囲、およびコピーを照合するかどうかなど、さまざまな印刷オプションを選択できます。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

IDOK または IDCANCEL。 IDCANCEL が返された場合は、Windows の[Commdlgextendederror](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)関数を呼び出して、エラーが発生したかどうかを確認します。

IDOK と IDCANCEL は、ユーザーが [OK] または [キャンセル] ボタンを選択したかどうかを示す定数です。

### <a name="remarks"></a>Remarks

`m_pd`構造体のメンバーを設定することによって、さまざまな印刷ダイアログオプションを初期化する場合は、 `DoModal`を呼び出す前に、ダイアログオブジェクトが構築された後にこの操作を行う必要があります。

を呼び出し`DoModal`た後、他のメンバー関数を呼び出して、ユーザーがダイアログボックスに入力した設定または情報を取得できます。

*Bprintsetuponly*を FALSE に設定してコンストラクターを呼び出すと、PD_RETURNDC フラグが自動的に使用されることに注意してください。 、 `DoModal` `m_pd.hDC`、または`GetPrinterDC`を呼び出すと、プリンターの DC がに返されます。 `GetDefaults` この DC は、の呼び出し元によって[DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)への`CPrintDialog`呼び出しを使用して解放する必要があります。

### <a name="example"></a>例

  [CPrintDialog:: Createプリンター dc](#createprinterdc)の例を参照してください。

##  <a name="getcopies"></a>  CPrintDialog::GetCopies

要求されたコピーの数を取得します。

```
int GetCopies() const;
```

### <a name="return-value"></a>戻り値

要求されたコピーの数。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、要求されたコピーの数を取得するために、この関数を呼び出します。

### <a name="example"></a>例

  [CPrintDialog::P rintcollate](#printcollate)の例を参照してください。

##  <a name="getdefaults"></a>CPrintDialog::GetDefaults

ダイアログボックスを表示せずに、既定のプリンターのデバイスの既定値を取得します。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>戻り値

関数が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

取得した値は`m_pd`構造体に配置されます。

場合によっては、この関数を呼び出すと、 *bprintsetuponly*が FALSE に設定されたの`CPrintDialog` [コンストラクター](#cprintdialog)が呼び出されます。 このような場合、プリンター DC と`hDevNames`および`hDevMode` ( `m_pd`データメンバー内にある2つのハンドル) が自動的に割り当てられます。

`CPrintDialog`のコンストラクターが*bprintsetuponly*を FALSE に設定して呼び出された場合、この関数は`hDevNames`を呼び出し元`m_pd.hDevNames`に`m_pd.hDevMode`返すだけで`hDevMode`なく、にも配置されます`m_pd.hDC`。 `CPrintDialog`オブジェクトの操作が完了したら、プリンター DC を削除して、ハンドルに対して Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)関数を呼び出す必要があります。

### <a name="example"></a>例

このコード片では、既定のプリンターのデバイスコンテキストを取得し、ユーザーにプリンターの解像度を1インチあたりのドット数で報告します。 (プリンターの機能のこの属性は、多くの場合 DPI と呼ばれます)。

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

現在選択されているプリンターデバイスの名前を取得します。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>戻り値

現在選択されているプリンターの名前。

### <a name="remarks"></a>Remarks

[DoModal](#domodal)を呼び出した後にこの関数を呼び出して、現在選択されているプリンターの名前を取得します。または、 [GetDefaults](#getdefaults)を呼び出して、既定のプリンターの現在のデバイスの既定値を取得します。 [CDC:: createdc](../../mfc/reference/cdc-class.md#createdc)への呼び出し`GetDeviceName`で、によっ`lpszDeviceName`て返される`CString`オブジェクトへのポインターを、の値として使用します。

### <a name="example"></a>例

このコード片は、プリンターが使用するスプーラ名と共に、ユーザーの既定のプリンター名と接続先のポートを示しています。 このコードでは、"既定のプリンターは、winspool を使用して、\ \\\ ホームにある HP LaserJet IIIP です。" というメッセージボックスが表示されることがあります。

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

`DEVMODE`構造体を取得します。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>戻り値

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)データ構造体。これには、印刷ドライバーのデバイスの初期化と環境に関する情報が含まれます。 この構造体によって取得されるメモリは、Windows [globalunlock](/windows/win32/api/winbase/nf-winbase-globalunlock)関数を使用してロック解除する必要があります。これについては、Windows SDK を参照してください。

### <a name="remarks"></a>Remarks

[DoModal](#domodal)または[GetDefaults](#getdefaults)を呼び出した後に、この関数を呼び出して、印刷デバイスに関する情報を取得します。

### <a name="example"></a>例

  [CPrintDialog::P rintcollate](#printcollate)の例を参照してください。

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

現在選択されているプリンタードライバーの名前を取得します。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>戻り値

システム定義のドライバー名を指定する。`CString`

### <a name="remarks"></a>Remarks

システム定義のプリンターデバイスドライバーの名前を取得するには、 [DoModal](#domodal)または[GetDefaults](#getdefaults)を呼び出した後にこの関数を呼び出します。 [CDC:: createdc](../../mfc/reference/cdc-class.md#createdc)への呼び出し`GetDriverName`で、によっ`lpszDriverName`て返される`CString`オブジェクトへのポインターを、の値として使用します。

### <a name="example"></a>例

  [CPrintDialog:: GetDeviceName](#getdevicename)の例を参照してください。

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

印刷範囲の開始ページを取得します。

```
int GetFromPage() const;
```

### <a name="return-value"></a>戻り値

印刷するページ範囲の開始ページ番号。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、この関数を呼び出して、印刷するページ範囲の開始ページ番号を取得します。

### <a name="example"></a>例

  [CPrintDialog:: m_pd](#m_pd)の例を参照してください。

##  <a name="getportname"></a>  CPrintDialog::GetPortName

現在選択されているプリンターポートの名前を取得します。

```
CString GetPortName() const;
```

### <a name="return-value"></a>戻り値

現在選択されているプリンターポートの名前。

### <a name="remarks"></a>Remarks

現在選択されているプリンターポートの名前を取得するために、 [DoModal](#domodal)または[GetDefaults](#getdefaults)を呼び出した後に、この関数を呼び出します。

### <a name="example"></a>例

  [CPrintDialog:: GetDeviceName](#getdevicename)の例を参照してください。

##  <a name="getprinterdc"></a>CPrintDialog:: Getプリンター Dc

プリンターデバイスコンテキストへのハンドルを取得します。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、プリンターデバイスコンテキストへのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

`CPrintDialog`コンストラクターの*bprintsetuponly*パラメーターが FALSE の場合 ([ `GetPrinterDC`印刷] ダイアログボックスが表示されることを示す)、はプリンターデバイスコンテキストへのハンドルを返します。 使用が完了したら、Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)関数を呼び出して、デバイスコンテキストを削除する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

印刷範囲の終了ページを取得します。

```
int GetToPage() const;
```

### <a name="return-value"></a>戻り値

印刷するページ範囲の終了ページ番号。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、この関数を呼び出して、印刷するページ範囲の終了ページ番号を取得します。

### <a name="example"></a>例

  [CPrintDialog:: m_pd](#m_pd)の例を参照してください。

##  <a name="m_pd"></a>CPrintDialog::m_pd

ダイアログオブジェクトの特性を格納するメンバーを持つ構造体。

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Remarks

`CPrintDialog`オブジェクトを構築した後、を`m_pd`使用して、ダイアログボックスのさまざまな側面を設定してから、 [DoModal](#domodal)メンバー関数を呼び出すことができます。 `m_pd`構造の詳細については、Windows SDK の「 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) 」を参照してください。

`m_pd`データメンバーを直接変更すると、すべての既定の動作がオーバーライドされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

ドキュメントのすべてのページを印刷するかどうかを決定します。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>戻り値

ドキュメント内のすべてのページを印刷する場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、ドキュメント内のすべてのページを印刷するかどうかを判断するために、この関数を呼び出します。

### <a name="example"></a>例

  [CPrintDialog:: m_pd](#m_pd)の例を参照してください。

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

照合されたコピーが要求されるかどうかを決定します。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>戻り値

ユーザーがダイアログボックスの [部単位で印刷] チェックボックスをオンにした場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、この関数を呼び出して、プリンターがドキュメントのすべての印刷コピーを照合する必要があるかどうかを判断します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

指定した範囲のページだけを印刷するかどうかを決定します。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>戻り値

ドキュメント内のページの範囲だけを印刷する場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、この関数を呼び出して、文書内のページの範囲だけを印刷するかどうかを決定します。

### <a name="example"></a>例

  [CPrintDialog:: m_pd](#m_pd)の例を参照してください。

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

現在選択されている項目だけを印刷するかどうかを決定します。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>戻り値

選択した項目だけを印刷する場合は0以外の場合は。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を呼び出し`DoModal`た後に、現在選択されている項目だけを印刷するかどうかを判断するために、この関数を呼び出します。

### <a name="example"></a>例

  [CPrintDialog:: m_pd](#m_pd)の例を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 構造体](../../mfc/reference/cprintinfo-structure.md)
