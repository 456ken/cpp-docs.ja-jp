---
title: CDialog クラス
ms.date: 09/07/2019
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907607"
---
# <a name="cdialog-class"></a>CDialog クラス

画面上にダイアログボックスを表示するために使用される基本クラスです。

## <a name="syntax"></a>構文

```
class CDialog : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDialog:: CDialog](#cdialog)|`CDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDialog:: Create](#create)|`CDialog` オブジェクトを初期化します。 モードレスダイアログボックスを作成し、 `CDialog`オブジェクトにアタッチします。|
|[CDialog:: CreateIndirect](#createindirect)|メモリ内のダイアログボックステンプレートからモードレスダイアログボックスを作成します (リソースベースではありません)。|
|[CDialog::D oModal](#domodal)|モーダルダイアログボックスを呼び出し、完了した場合はを返します。|
|[CDialog::EndDialog](#enddialog)|モーダルダイアログボックスを閉じます。|
|[CDialog:: GetDefID](#getdefid)|ダイアログボックスの既定のプッシュボタンコントロールの ID を取得します。|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|ダイアログボックス内の指定されたダイアログボックスコントロールにフォーカスを移動します。|
|[CDialog::InitModalIndirect](#initmodalindirect)|リソースベースではなく、メモリ内のダイアログボックステンプレートからモーダルダイアログボックスを作成します。 パラメーターは、関数`DoModal`が呼び出されるまで格納されます。|
|[CDialog::MapDialogRect](#mapdialogrect)|四角形のダイアログボックス単位を画面単位に変換します。|
|[CDialog:: NextDlgCtrl](#nextdlgctrl)|ダイアログボックスの次のダイアログボックスコントロールにフォーカスを移動します。|
|[CDialog::OnInitDialog](#oninitdialog)|ダイアログボックスの初期化を強化するためにオーバーライドします。|
|[CDialog::OnSetFont](#onsetfont)|テキストを描画するときにダイアログボックスコントロールが使用するフォントを指定するためにオーバーライドします。|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|ダイアログボックスの前のダイアログボックスコントロールにフォーカスを移動します。|
|[CDialog:: SetDefID](#setdefid)|ダイアログボックスの既定のプッシュボタンコントロールを、指定したプッシュボタンに変更します。|
|[CDialog:: Sei Pid](#sethelpid)|ダイアログボックスの状況依存のヘルプ ID を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CDialog:: OnCancel](#oncancel)|[キャンセル] ボタンまたは ESC キー操作を実行するには、をオーバーライドします。 既定では、ダイアログボックスが`DoModal`閉じて、IDCANCEL が返されます。|
|[CDialog::OnOK](#onok)|をオーバーライドして、モーダルダイアログボックスで [OK] ボタンの操作を実行します。 既定では、ダイアログボックスが`DoModal`閉じて、IDOK が返されます。|

## <a name="remarks"></a>Remarks

ダイアログボックスには、モーダルとモードレスの2種類があります。 モーダルダイアログボックスは、アプリケーションを続行する前に、ユーザーが閉じる必要があります。 モードレスダイアログボックスを使用すると、ダイアログボックスを表示したり、ダイアログボックスをキャンセルしたり削除したりせずに、別のタスクに戻ることができます。

オブジェクトは、ダイアログテンプレート`CDialog`との派生クラスを組み合わせたものです。 `CDialog` ダイアログエディターを使用してダイアログテンプレートを作成し、リソースに格納します。次に、クラスの追加ウィザードを使用し`CDialog`て、から派生したクラスを作成します。

ダイアログボックスは、他のウィンドウと同様に、Windows からメッセージを受信します。 ダイアログボックスでは、ダイアログボックスのコントロールからの通知メッセージを処理することに特に興味があります。これは、ユーザーがダイアログボックスと対話する方法であるためです。 [クラスウィザード](mfc-class-wizard.md)を使用して、処理するメッセージを選択し、適切なメッセージマップエントリとメッセージハンドラーメンバー関数をクラスに追加します。 ハンドラーメンバー関数には、アプリケーション固有のコードを記述する必要があります。

必要に応じて、メッセージマップエントリとメンバー関数をいつでも手動で書き込むことができます。

最も単純なダイアログボックス以外では、ユーザーがダイアログボックスのコントロールに入力したデータを格納したり、ユーザーのデータを表示したりするために、派生したダイアログクラスにメンバー変数を追加します。 変数の追加ウィザードを使用すると、メンバー変数を作成し、コントロールに関連付けることができます。 同時に、変数の型と、各変数に許容される値の範囲を選択します。 コードウィザードでは、メンバー変数が派生ダイアログクラスに追加されます。

データマップは、メンバー変数とダイアログボックスのコントロールとの間のデータ交換を自動的に処理するために生成されます。 データマップには、ダイアログボックス内のコントロールを適切な値で初期化し、データを取得して、データを検証する関数が用意されています。

モーダルダイアログボックスを作成するには、派生ダイアログクラスのコンストラクターを使用してスタック上にオブジェクトを構築`DoModal`し、を呼び出してダイアログウィンドウとそのコントロールを作成します。 モードレスダイアログを作成する場合は、ダイアログクラス`Create`のコンストラクターでを呼び出します。

Windows SDK で説明されているように、 [dlgtemplate](/windows/win32/api/winuser/ns-winuser-dlgtemplate)データ構造を使用して、メモリ内にテンプレートを作成することもできます。 オブジェクト`CDialog`を構築した後、 [createindirect](#createindirect)を呼び出してモードレスダイアログボックスを作成するか、 [InitModalIndirect](#initmodalindirect)および[DoModal](#domodal)を呼び出してモーダルダイアログボックスを作成します。

Exchange および検証データマップは、新しいダイアログクラスに追加`CWnd::DoDataExchange`されるのオーバーライドで記述されます。 詳細については、 `CWnd` 「」の「[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) メンバー関数」を参照してください。

プログラマとフレームワークは、どちらも`DoDataExchange` [CWnd:: UpdateData](../../mfc/reference/cwnd-class.md#updatedata)を呼び出すことによって間接的に呼び出します。

フレームワークは、 `UpdateData`ユーザーが [OK] ボタンをクリックしてモーダルダイアログボックスを閉じると、を呼び出します。 ([キャンセル] ボタンがクリックされると、データは取得されません)。[OnInitDialog](#oninitdialog)の既定の実装では`UpdateData` 、コントロールの初期値を設定するためにもを呼び出します。 通常は、 `OnInitDialog`コントロールをさらに初期化するためにをオーバーライドします。 `OnInitDialog`は、すべてのダイアログコントロールが作成された後、ダイアログボックスが表示される直前に呼び出されます。

モーダルまたは`CWnd::UpdateData`モードレスのダイアログボックスの実行中に、いつでもを呼び出すことができます。

ダイアログボックスを手動で開発する場合は、必要なメンバー変数を派生したダイアログボックスクラスに自分で追加し、これらの値を設定または取得するメンバー関数を追加します。

モーダルダイアログボックスは、ユーザーが [OK] ボタンまたは [キャンセル] ボタンをクリックした`EndDialog`とき、またはコードがメンバー関数を呼び出したときに、自動的に閉じられます。

モードレスダイアログボックスを実装する場合は、常に`OnCancel`メンバー関数をオーバーライド`DestroyWindow`し、その中からを呼び出します。 基底クラス`CDialog::OnCancel` `EndDialog`はを呼び出さないでください。これにより、ダイアログボックスは非表示になりますが、破棄されません。 また、モードレスダイアログ`PostNcDestroy`ボックスは通常、**新しい**と共に割り当てられるため、**この**プロパティを削除するには、モードレスダイアログボックスに対してもオーバーライドする必要があります。 モーダルダイアログボックスは通常、フレーム上に構築され、 `PostNcDestroy`クリーンアップは必要ありません。

の`CDialog`詳細については、「[ダイアログボックス](../../mfc/dialog-boxes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cdialog"></a>CDialog:: CDialog

リソースベースのモーダルダイアログボックスを構築するには、コンストラクターのパブリックフォームを呼び出します。

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログボックステンプレートリソースの名前である null で終わる文字列を格納します。

*nIDTemplate*<br/>
ダイアログボックステンプレートリソースの ID 番号を格納します。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親またはオーナーウィンドウオブジェクト ( [CWnd](../../mfc/reference/cwnd-class.md)型) を指します。 NULL の場合は、ダイアログオブジェクトの親ウィンドウがメインアプリケーションウィンドウに設定されます。

### <a name="remarks"></a>Remarks

コンストラクターの1つの形式は、テンプレート名によってダイアログリソースへのアクセスを提供します。 もう1つのコンストラクターは、テンプレート ID 番号によってアクセスを提供します。通常は、 **IDD_** プレフィックス (たとえば、IDD_DIALOG1) を使用します。

メモリ内のテンプレートからモーダルダイアログボックスを構築するには、最初にパラメーターなしのプロテクトコンストラクターを`InitModalIndirect`呼び出し、次にを呼び出します。

上記のメソッドのいずれかを使用してモーダルダイアログボックスを構築`DoModal`した後、を呼び出します。

モードレスダイアログボックスを構築するには、 `CDialog`コンストラクターの protected 形式を使用します。 このコンストラクターは、モードレスダイアログボックスを実装するために独自のダイアログボックスクラスを派生させる必要があるため、保護されています。 モードレスダイアログボックスの構築は、2段階のプロセスです。 最初にコンストラクターを呼び出します。次に、 `Create`メンバー関数を呼び出して、リソースベースのダイアログボックスを作成`CreateIndirect`するか、を呼び出して、メモリ内のテンプレートからダイアログボックスを作成します。

##  <a name="create"></a>CDialog:: Create

を`Create`呼び出して、リソースからダイアログボックステンプレートを使用して、モードレスダイアログボックスを作成します。

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログボックステンプレートリソースの名前である null で終わる文字列を格納します。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親ウィンドウオブジェクト ( [CWnd](../../mfc/reference/cwnd-class.md)型) をポイントします。 NULL の場合は、ダイアログオブジェクトの親ウィンドウがメインアプリケーションウィンドウに設定されます。

*nIDTemplate*<br/>
ダイアログボックステンプレートリソースの ID 番号を格納します。

### <a name="return-value"></a>戻り値

ダイアログボックスの作成と初期化が正常に完了した場合、どちらの形式でも0以外が返されます。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

コンストラクターの内部にを呼び`Create`出すか、コンストラクターが呼び出された後に呼び出しを呼び出すことができます。

テンプレート名または`Create`テンプレート ID 番号 (たとえば、IDD_DIALOG1) によってダイアログボックステンプレートリソースにアクセスするために、メンバー関数の2つの形式が用意されています。

どちらの形式でも、親ウィンドウオブジェクトへのポインターを渡します。 *PParentWnd*が NULL の場合、ダイアログボックスは親ウィンドウまたはオーナーウィンドウがメインアプリケーションウィンドウに設定された状態で作成されます。

この`Create`メンバー関数は、ダイアログボックスを作成した直後に戻ります。

親ウィンドウが作成されたときにダイアログボックスが表示されるようにするには、ダイアログボックステンプレートで WS_VISIBLE スタイルを使用します。 それ以外の場合は`ShowWindow`、を呼び出す必要があります。 ダイアログボックスのスタイルとアプリケーションの詳細については、 *MFC リファレンス*の Windows SDK と[ウィンドウのスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)で、 [dlgtemplate](/windows/win32/api/winuser/ns-winuser-dlgtemplate)構造体を参照してください。

`CWnd::DestroyWindow` 関数`Create`によって作成されたダイアログボックスを破棄するには、関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>  CDialog::CreateIndirect

メモリ内のダイアログボックステンプレートからモードレスダイアログボックスを作成するには、このメンバー関数を呼び出します。

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*Lpのテンプレート*<br/>
ダイアログボックスの作成に使用されるダイアログボックステンプレートを格納しているメモリを指します。 このテンプレートは、「Windows SDK」で説明されているように、 [Dlgtemplate](/windows/win32/api/winuser/ns-winuser-dlgtemplate)構造体とコントロール情報の形式になっています。

*pParentWnd*<br/>
ダイアログオブジェクトの親ウィンドウオブジェクト ( [CWnd](../../mfc/reference/cwnd-class.md)型) を指します。 NULL の場合は、ダイアログオブジェクトの親ウィンドウがメインアプリケーションウィンドウに設定されます。

*Lpの Init*<br/>
DLGINIT リソースを指します。

*Hのテンプレート*<br/>
ダイアログボックステンプレートを含むグローバルメモリへのハンドルを格納します。 このテンプレートは、ダイアログボックス内の`DLGTEMPLATE`各コントロールの構造とデータの形式です。

### <a name="return-value"></a>戻り値

ダイアログボックスが作成され、正常に初期化された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この`CreateIndirect`メンバー関数は、ダイアログボックスを作成した直後に戻ります。

親ウィンドウが作成されたときにダイアログボックスが表示されるようにするには、ダイアログボックステンプレートで WS_VISIBLE スタイルを使用します。 それ以外の場合は`ShowWindow` 、を呼び出すと、が表示されます。 テンプレートで他のダイアログボックススタイルを指定する方法の詳細については、Windows SDK の「 [Dlgtemplate](/windows/win32/api/winuser/ns-winuser-dlgtemplate)構造体」を参照してください。

`CWnd::DestroyWindow` 関数`CreateIndirect`によって作成されたダイアログボックスを破棄するには、関数を使用します。

ActiveX コントロールを含むダイアログボックスでは、DLGINIT リソースに追加情報が提供されます。

##  <a name="domodal"></a>  CDialog::DoModal

モーダルダイアログボックスを呼び出し、完了したらダイアログボックスの結果を返すには、このメンバー関数を呼び出します。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

ダイアログボックスを閉じるために使用される、 [CDialog:: EndDialog](#enddialog)メンバー関数に渡された*nresult*パラメーターの値を指定する**int**値。 関数でダイアログボックスを作成できなかった場合、または IDABORT (他のエラーが発生した場合) の戻り値は-1 です。この場合、出力ウィンドウには、 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)からのエラー情報が含まれます。

### <a name="remarks"></a>Remarks

このメンバー関数は、ダイアログボックスがアクティブになっている間、ユーザーとのすべての対話を処理します。 これにより、ダイアログボックスがモーダルになります。つまり、ダイアログボックスが閉じられるまで、ユーザーは他のウィンドウと対話できません。

ユーザーがダイアログボックスのプッシュボタンの1つ ([OK] や [キャンセル] など) をクリックすると、 [OnOK](#onok)や[OnCancel](#oncancel)などのメッセージハンドラーメンバー関数が呼び出され、ダイアログボックスを閉じようとします。 既定`OnOK`のメンバー関数は、ダイアログボックスのデータを検証および更新し、結果 IDOK でダイアログボックスを閉じます。 `OnCancel`既定のメンバー関数は、を検証または更新せずに result IDCANCEL を使用してダイアログボックスを閉じます。ダイアログボックスのデータ。 これらのメッセージハンドラー関数をオーバーライドして、動作を変更できます。

> [!NOTE]
> `PreTranslateMessage`は、モーダルダイアログボックスのメッセージ処理のために呼び出されるようになりました。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

モーダルダイアログボックスを終了するには、このメンバー関数を呼び出します。

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>パラメーター

*n 結果*<br/>
ダイアログボックスからの`DoModal`呼び出し元に返される値を格納します。

### <a name="remarks"></a>Remarks

このメンバー関数は、の`DoModal`戻り値として*nresult*を返します。 モーダルダイアログボックスが`EndDialog`作成されるたびに処理を完了するには、関数を使用する必要があります。

[OnInitDialog](#oninitdialog) でも`EndDialog` 、いつでもを呼び出すことができます。その場合は、ダイアログボックスが表示される前、または入力フォーカスが設定される前に閉じる必要があります。

`EndDialog`では、ダイアログボックスがすぐに閉じられることはありません。 代わりに、現在のメッセージハンドラーが戻るとすぐにダイアログボックスを閉じるように指示するフラグを設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

`GetDefID`メンバー関数を呼び出して、ダイアログボックスの既定のプッシュボタンコントロールの ID を取得します。

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>戻り値

32ビット値 ( `DWORD`)。 既定のプッシュボタンに ID 値が設定されている場合、上位ワードには DC_HASDEFID が含まれ、下位ワードには ID 値が含まれます。 既定のプッシュボタンに ID 値がない場合、戻り値は0になります。

### <a name="remarks"></a>Remarks

通常、これは [OK] ボタンです。

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

ダイアログボックス内の指定されたコントロールにフォーカスを移動します。

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>パラメーター

*pWndCtrl*<br/>
フォーカスを受け取るウィンドウ (コントロール) を識別します。

### <a name="remarks"></a>Remarks

*PWndCtrl*として渡すコントロール (子ウィンドウ) へのポインターを取得するには`CWnd::GetDlgItem` 、 [CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインターを返すメンバー関数を呼び出します。

### <a name="example"></a>例

  [CWnd:: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)の例を参照してください。

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

メモリ内に構築したダイアログボックステンプレートを使用してモーダルダイアログオブジェクトを初期化するには、このメンバー関数を呼び出します。

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*Lpのテンプレート*<br/>
ダイアログボックスの作成に使用されるダイアログボックステンプレートを格納しているメモリを指します。 このテンプレートは、「Windows SDK」で説明されているように、 [Dlgtemplate](/windows/win32/api/winuser/ns-winuser-dlgtemplate)構造体とコントロール情報の形式になっています。

*Hのテンプレート*<br/>
ダイアログボックステンプレートを含むグローバルメモリへのハンドルを格納します。 このテンプレートは、ダイアログボックス内の`DLGTEMPLATE`各コントロールの構造とデータの形式です。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親またはオーナーウィンドウオブジェクト ( [CWnd](../../mfc/reference/cwnd-class.md)型) を指します。 NULL の場合は、ダイアログオブジェクトの親ウィンドウがメインアプリケーションウィンドウに設定されます。

*Lpの Init*<br/>
DLGINIT リソースを指します。

### <a name="return-value"></a>戻り値

ダイアログオブジェクトが正常に作成され初期化された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

モーダルダイアログボックスを間接的に作成するには、まずメモリのグローバルブロックを割り当てて、ダイアログボックステンプレートを使用します。 次に、空`CDialog`のコンストラクターを呼び出して、ダイアログボックスオブジェクトを作成します。 次に、 `InitModalIndirect`を呼び出して、メモリ内ダイアログボックステンプレートへのハンドルを格納します。 [Windows] ダイアログボックスは、後で[DoModal](#domodal)メンバー関数が呼び出されたときに作成されて表示されます。

ActiveX コントロールを含むダイアログボックスでは、DLGINIT リソースに追加情報が提供されます。

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

を呼び出して、四角形のダイアログボックスの単位を画面単位に変換します。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
変換するダイアログボックス座標を格納している[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトをポイントします。

### <a name="remarks"></a>Remarks

ダイアログボックスの単位は、ダイアログボックスのテキストに使用されるフォントの平均の幅と高さから派生した、現在のダイアログボックスの基本単位に関して示されています。 1つの水平方向の単位はダイアログボックスの基本幅の単位の1番目で、1つの垂直方向の単位はダイアログボックスの基本高さの単位の8分の1です。

Windows `GetDialogBaseUnits`の関数はシステムフォントのサイズ情報を返しますが、リソース定義ファイルで DS_SETFONT スタイルを使用する場合は、各ダイアログボックスに別のフォントを指定できます。 Windows `MapDialogRect`関数は、このダイアログボックスに適切なフォントを使用します。

この`MapDialogRect`メンバー関数は、 *lpRect*内のダイアログボックス単位を画面単位 (ピクセル) で置き換えます。これにより、四角形を使用してダイアログボックスを作成したり、ボックス内にコントロールを配置したりすることができます。

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

ダイアログボックスの次のコントロールにフォーカスを移動します。

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Remarks

フォーカスがダイアログボックスの最後のコントロールにある場合は、最初のコントロールに移動します。

##  <a name="oncancel"></a>CDialog:: OnCancel

フレームワークは、ユーザーが **[キャンセル**] をクリックするか、モーダルまたはモードレスダイアログボックスで ESC キーを押すと、このメソッドを呼び出します。

```
virtual void OnCancel();
```

### <a name="remarks"></a>Remarks

ユーザーがダイアログボックスを閉じるときに、 **[キャンセル**] をクリックするか ESC キーを押すと、このメソッドをオーバーライドして操作 (古いデータの復元など) を実行します。 既定では、 [EndDialog](#enddialog)を呼び出し、 [DoModal](#domodal)が IDCANCEL を返すようにすることで、モーダルダイアログボックスを閉じます。

モードレスダイアログボックスに **[キャンセル**] ボタンを実装する場合は、 `OnCancel`メソッドをオーバーライドし、その中で[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)を呼び出す必要があります。 基底クラスのメソッドを呼び出さないでください。を`EndDialog`呼び出すと、ダイアログボックスは非表示になりますが、破棄はされません。

> [!NOTE]
>  Windows XP でコンパイルされたプログラムで`CFileDialog`オブジェクトを使用する場合、このメソッドをオーバーライドすることはできません。 の詳細`CFileDialog`については、「 [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

このメソッドは、メッセージへの応答`WM_INITDIALOG`として呼び出されます。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>戻り値

アプリケーションがダイアログボックスのコントロールのいずれかに入力フォーカスを設定したかどうかを指定します。 が`OnInitDialog` 0 以外の値を返した場合、Windows は、ダイアログボックスの最初のコントロールである既定の場所に入力フォーカスを設定します。 アプリケーションは、ダイアログボックス内のコントロールのいずれかに入力フォーカスを明示的に設定している場合にのみ、0を返すことができます。

### <a name="remarks"></a>Remarks

Windows は、 `WM_INITDIALOG`ダイアログボックスが表示される直前に発生する、 [Create](#create)、 [createindirect](#createindirect)、または[DoModal](#domodal)の呼び出し中にダイアログボックスにメッセージを送信します。

ダイアログボックスが初期化されるときに特別な処理を実行する場合は、このメソッドをオーバーライドします。 オーバーライドされたバージョンでは、最初に`OnInitDialog`基本クラスを呼び出しますが、その戻り値は無視します。 通常は、オーバーライド`TRUE`されたメソッドからを返します。

Windows は、 `OnInitDialog`すべての Microsoft Foundation Class ライブラリダイアログボックスに共通する標準のグローバルダイアログボックスのプロシージャを使用して、関数を呼び出します。 メッセージマップを介してこの関数を呼び出すことはないため、このメソッドのメッセージマップエントリは必要ありません。

> [!NOTE]
> Windows Vista 以降のオペレーティングシステムでコンパイルさ`CFileDialog`れるプログラムでオブジェクトを使用する場合、このメソッドをオーバーライドすることはできません。 Windows Vista 以降でに`CFileDialog`加えられた変更の詳細については、「 [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>  CDialog::OnOK

ユーザーが **[OK** ] ボタン (ID が IDOK のボタン) をクリックしたときに呼び出されます。

```
virtual void OnOK();
```

### <a name="remarks"></a>Remarks

**[OK** ] ボタンがアクティブになったときにアクションを実行するには、このメソッドをオーバーライドします。 ダイアログボックスに自動データ検証と exchange が含まれている場合、このメソッドの既定の実装はダイアログボックスデータを検証し、アプリケーション内の適切な変数を更新します。

モードレスダイアログボックスに **[OK** ] ボタンを実装する場合は、 `OnOK`メソッドをオーバーライドし、その中で[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)を呼び出す必要があります。 基底クラスのメソッドを呼び出さないでください。このメソッドは、ダイアログボックスが非表示になりますが、破棄されないよう[にするためです。](#enddialog)

> [!NOTE]
>  Windows XP でコンパイルされたプログラムで`CFileDialog`オブジェクトを使用する場合、このメソッドをオーバーライドすることはできません。 の詳細`CFileDialog`については、「 [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

テキストを描画するときにダイアログボックスコントロールが使用するフォントを指定します。

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
からこのダイアログボックスのすべてのコントロールの既定のフォントとして使用されるフォントへのポインターを指定します。

### <a name="remarks"></a>Remarks

ダイアログボックスでは、すべてのコントロールの既定値として、指定したフォントが使用されます。

ダイアログエディターでは、通常、ダイアログボックスのテンプレートリソースの一部としてダイアログボックスフォントが設定されます。

> [!NOTE]
> Windows Vista 以降のオペレーティングシステムでコンパイルさ`CFileDialog`れるプログラムでオブジェクトを使用する場合、このメソッドをオーバーライドすることはできません。 Windows Vista 以降でに`CFileDialog`加えられた変更の詳細については、「 [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)」を参照してください。

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

ダイアログボックスの前のコントロールにフォーカスを設定します。

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Remarks

フォーカスがダイアログボックスの最初のコントロールにある場合は、ボックス内の最後のコントロールに移動します。

##  <a name="setdefid"></a>CDialog:: SetDefID

ダイアログボックスの既定のプッシュボタンコントロールを変更します。

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
既定値になるプッシュボタンコントロールの ID を指定します。

##  <a name="sethelpid"></a>CDialog:: Sei Pid

ダイアログボックスの状況依存のヘルプ ID を設定します。

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>パラメーター

*nIDR*<br/>
状況依存のヘルプ ID を指定します。

## <a name="see-also"></a>関連項目

[MFC のサンプル DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
