---
title: CRegKey クラス
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: 1215c66f1f40cfbc96b813d4eb5084f07698bc01
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58778300"
---
# <a name="cregkey-class"></a>CRegKey クラス

このクラスは、システム レジストリのエントリを操作するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CRegKey
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|コンストラクターです。|
|[CRegKey:: ~ CRegKey](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRegKey::Attach](#attach)|HKEY をアタッチするには、このメソッドを呼び出す、`CRegKey`オブジェクトを設定して、 [m_hKey](#m_hkey)メンバーを識別するハンドル`hKey`します。|
|[CRegKey::Close](#close)|解放するには、このメソッドを呼び出し、 [m_hKey](#m_hkey)メンバーが処理し、NULL に設定します。|
|[CRegKey::Create](#create)|としてのサブキーが存在しない場合は、指定したキーを作成するには、このメソッドを呼び出す`hKeyParent`します。|
|[CRegKey::DeleteSubKey](#deletesubkey)|指定したキーをレジストリから削除するには、このメソッドを呼び出します。|
|[CRegKey::DeleteValue](#deletevalue)|値フィールドを削除するには、このメソッドを呼び出す[m_hKey](#m_hkey)します。|
|[CRegKey::Detach](#detach)|デタッチするには、このメソッドを呼び出す、 [m_hKey](#m_hkey)からメンバーのハンドル、`CRegKey`オブジェクトし、設定`m_hKey`を NULL にします。|
|[CRegKey::EnumKey](#enumkey)|開いているレジストリ キーのサブキーの列挙には、このメソッドを呼び出します。|
|[CRegKey::Flush](#flush)|すべての開いているレジストリ キーの属性をレジストリに書き込むには、このメソッドを呼び出します。|
|[CRegKey::GetKeySecurity](#getkeysecurity)|開いているレジストリ キーを保護するセキュリティ記述子のコピーを取得するには、このメソッドを呼び出します。|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|このメソッドでは、属性またはレジストリ キーの内容の変更について、呼び出し元に通知します。|
|[CRegKey::Open](#open)|指定したキーを開き、設定するには、このメソッドを呼び出す[m_hKey](#m_hkey)にこのキーのハンドル。|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|指定された値の名前のバイナリ データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|DWORD データ値を指定した名前を取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|GUID データ値を指定した名前を取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|指定された値名の複数行文字列のデータを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|QWORD データが指定された値の名前を取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryStringValue](#querystringvalue)|指定された値名の文字列データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryValue](#queryvalue)|指定した値のフィールドのデータを取得するには、このメソッドを呼び出す[m_hKey](#m_hkey)します。 このメソッドの以前のバージョンでは、現在サポートされていませんされ、されずとしてマークされます。|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|指定したキーをレジストリから削除し、すべてのサブキーを明示的に削除するには、このメソッドを呼び出します。|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|レジストリ キーのバイナリ値を設定するには、このメソッドを呼び出します。|
|[CRegKey::SetDWORDValue](#setdwordvalue)|レジストリ キーの DWORD 値を設定するには、このメソッドを呼び出します。|
|[CRegKey::SetGUIDValue](#setguidvalue)|レジストリ キーの GUID 値を設定するには、このメソッドを呼び出します。|
|[CRegKey::SetKeySecurity](#setkeysecurity)|レジストリ キーのセキュリティを設定するには、このメソッドを呼び出します。|
|[CRegKey::SetKeyValue](#setkeyvalue)|指定したキーの指定した値のフィールドにデータを格納するには、このメソッドを呼び出します。|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|レジストリ キーの複数行文字列の値を設定するには、このメソッドを呼び出します。|
|[CRegKey::SetQWORDValue](#setqwordvalue)|レジストリ キーの QWORD 値を設定するには、このメソッドを呼び出します。|
|[CRegKey::SetStringValue](#setstringvalue)|レジストリ キーの文字列値を設定します。|
|[CRegKey::SetValue](#setvalue)|指定された値 フィールドのデータを格納するには、このメソッドを呼び出す[m_hKey](#m_hkey)します。 このメソッドの以前のバージョンでは、現在サポートされていませんされ、されずとしてマークされます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|変換を`CRegKey`HKEY するオブジェクト。|
|[CRegKey::operator =](#operator_eq)|代入演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|関連付けられているレジストリ キーのハンドルが含まれています、`CRegKey`オブジェクト。|
|[CRegKey::m_pTM](#m_ptm)|ポインター`CAtlTransactionManager`オブジェクト|

## <a name="remarks"></a>Remarks

`CRegKey` 作成すると、システム レジストリのキーと値を削除するメソッドを提供します。 レジストリには、インストールに固有の一連ソフトウェアのバージョン番号、インストールされているハードウェア、および COM オブジェクトの物理的な論理マッピングなど、システム コンポーネントの定義にはが含まれています。

`CRegKey` 特定のコンピューターのシステム レジストリに対してプログラミング インターフェイスを提供します。 たとえば、特定のレジストリ キーを開くには、呼び出す`CRegKey::Open`します。 取得したり、データ値を変更したりするには、呼び出す`CRegKey::QueryValue`または`CRegKey::SetValue`、それぞれします。 キーを閉じるには、呼び出す`CRegKey::Close`します。

キーを閉じると、そのレジストリ データが書き込まれます (フラッシュ) ハード _ ディスク。 このプロセスは数秒をかかります。 呼び出すことができる場合、アプリケーションは、ハード_ディスクにレジストリ データを明示的に記述する必要があります、 [RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) Win32 関数。 ただし、`RegFlushKey`多くのシステム リソースを使用し、どうしても必要な場合にのみ呼び出す必要があります。

> [!IMPORTANT]
>  レジストリの場所を指定する呼び出し元を許可するすべてのメソッドでは、信頼できないデータを読み取る可能性があります。 ようにするメソッドを使用して、 [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)この関数が NULL 終端である文字列を明示的に処理しないの考慮事項を考慮する必要があります。 呼び出し元のコードの両方の条件をチェックする必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="attach"></a>  CRegKey::Attach

HKEY をアタッチするには、このメソッドを呼び出す、`CRegKey`オブジェクトを設定して、 [m_hKey](#m_hkey)メンバーを識別するハンドル*hKey*します。

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
レジストリ キーのハンドル。

### <a name="remarks"></a>Remarks

`Attach` 場合はアサート`m_hKey`以外の場合します。

##  <a name="close"></a>  CRegKey::Close

解放するには、このメソッドを呼び出し、 [m_hKey](#m_hkey)メンバーが処理し、NULL に設定します。

```
LONG Close() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS; を返しますそれ以外の場合、エラー値を返します。

##  <a name="create"></a>  CRegKey::Create

としてのサブキーが存在しない場合は、指定したキーを作成するには、このメソッドを呼び出す*hKeyParent*します。

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*hKeyParent*<br/>
オープンするキーのハンドル。

*lpszKeyName*<br/>
作成または開かれたキーの名前を指定します。 この名前のサブキーである必要があります*hKeyParent*します。

*lpszClass*<br/>
作成または開くキーのクラスを指定します。 既定値は、REG_NONE します。

*dwOptions*<br/>
キーのオプション。 既定値は、REG_OPTION_NON_VOLATILE です。 使用可能な値と説明の一覧は、次を参照してください。 [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) Windows SDK に含まれています。

*samDesired*<br/>
キーのセキュリティのアクセス。 既定値は KEY_READ &#124; KEY_WRITE します。 使用可能な値と説明の一覧は、次を参照してください。`RegCreateKeyEx`します。

*lpSecAttr*<br/>
ポインターを[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)キーのハンドルを子プロセスが継承できるかどうかを示す構造体。 既定では、このパラメーターが NULL (つまり、ハンドルを継承することはできませんです)。

*lpdwDisposition*<br/>
[out]NULL 以外の場合は、REG_CREATED_NEW_KEY (キーが存在せず作成した場合) またはポインターを取得し、(キーが存在し、開かれた) 場合。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返し、キーを開きます。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

`Create` 設定、 [m_hKey](#m_hkey)メンバーをこのキーのハンドル。

##  <a name="cregkey"></a>  CRegKey::CRegKey

コンストラクターです。

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
`CRegKey` オブジェクトへの参照。

*hKey*<br/>
レジストリ キーへのハンドル。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

新しい `CRegKey` オブジェクトを作成します。 既存のオブジェクトを作成できます`CRegKey`オブジェクト、またはレジストリ キーを識別するハンドル。

##  <a name="dtor"></a>  CRegKey:: ~ CRegKey

デストラクターです。

```
~CRegKey() throw();
```

### <a name="remarks"></a>Remarks

デストラクターのリリース`m_hKey`します。

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

指定したキーをレジストリから削除するには、このメソッドを呼び出します。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>パラメーター

*lpszSubKey*<br/>
削除するキーの名前を指定します。 この名前のサブキーである必要があります[m_hKey](#m_hkey)します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

`DeleteSubKey` サブキーがキーの削除のみできません。 キーにサブキーがある場合は、呼び出す[ある](#recursedeletekey)代わりにします。

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

値フィールドを削除するには、このメソッドを呼び出す[m_hKey](#m_hkey)します。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>パラメーター

*lpszValue*<br/>
削除する値のフィールドを指定します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

##  <a name="detach"></a>  CRegKey::Detach

デタッチするには、このメソッドを呼び出す、 [m_hKey](#m_hkey)からメンバーのハンドル、`CRegKey`オブジェクトし、設定`m_hKey`を NULL にします。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>戻り値

関連付けられている、HKEY、`CRegKey`オブジェクト。

##  <a name="enumkey"></a>  CRegKey::EnumKey

開いているレジストリ キーのサブキーの列挙には、このメソッドを呼び出します。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
サブキーのインデックス。 このパラメーターは、最初の呼び出しの 0 にする必要があります、後続の呼び出しだけインクリメントされます。

*pszName*<br/>
終端の null 文字を含む、サブキーの名前を受け取るバッファーへのポインター。 バッファーに完全なキーの階層ではないサブキーの名前のみがコピーされます。

*pnNameLength*<br/>
指定したバッファーの Tchar で、サイズを指定する変数へのポインター、 *pszName*パラメーター。 このサイズは、終端の null 文字を含める必要があります。 メソッドが返す場合は、変数が指す*戻る*バッファーに格納されている文字の数が含まれています。 返されるカウントでは、終端の null 文字は含まれません。

*pftLastWriteTime*<br/>
時間を受信する変数へのポインター、列挙するサブキーに最後に書き込んだ。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

サブキーを列挙するために呼び出す`CRegKey::EnumKey`インデックスはゼロにします。 インデックスの値をインクリメントし、メソッドが戻る ERROR_NO_MORE_ITEMS までを繰り返します。 詳細については、次を参照してください。 [RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) Windows SDK に含まれています。

##  <a name="flush"></a>  CRegKey::Flush

すべての開いているレジストリ キーの属性をレジストリに書き込むには、このメソッドを呼び出します。

```
LONG Flush() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) Windows SDK に含まれています。

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

開いているレジストリ キーを保護するセキュリティ記述子のコピーを取得するには、このメソッドを呼び出します。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>パラメーター

*si*<br/>
[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)要求されたセキュリティ情報を示す値。

*psd*<br/>
要求されたセキュリティ記述子のコピーを受け取るバッファーへのポインター。

*pnBytes*<br/>
指し示されるバッファーのバイト単位のサイズを*psd*します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 メソッドが失敗した場合、戻り値は 0 以外のエラー コードが WINERROR で定義されているは。H.

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity)します。

##  <a name="m_hkey"></a>  CRegKey::m_hKey

関連付けられているレジストリ キーのハンドルが含まれています、`CRegKey`オブジェクト。

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

ポインターを`CAtlTransactionManager`オブジェクト。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Remarks

##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue

このメソッドでは、属性またはレジストリ キーの内容の変更について、呼び出し元に通知します。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>パラメーター

*bWatchSubtree*<br/>
指定したキーとそのすべてのサブキーで、または指定したキーでのみ変更をレポートするかどうかを示すフラグを指定します。 このパラメーターが TRUE の場合、メソッドは、キーおよびそのサブキーに変更を報告します。 パラメーターが FALSE の場合、メソッドは、キーの変更のみを報告します。

*dwNotifyFilter*<br/>
変更を制御するフラグのセットを報告するかを指定します。 このパラメーターは、次の値の組み合わせを指定できます。

|[値]|説明|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|サブキーが追加または削除された場合、呼び出し元に通知します。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|セキュリティ記述子の情報など、キーの属性の変更の呼び出し元に通知します。|
|REG_NOTIFY_CHANGE_LAST_SET|キーの値への変更の呼び出し元に通知します。 これには、追加や、値を削除する既存の値の変更を含めることができます。|
|REG_NOTIFY_CHANGE_SECURITY|キーのセキュリティ記述子への変更の呼び出し元に通知します。|

*hEvent*<br/>
イベントに対するハンドル。 場合、 *bAsync*パラメーターが TRUE の場合、メソッドからすぐに、このイベントを通知することによって変更が報告されます。 場合*bAsync* false で、 *hEvent*は無視されます。

*bAsync*<br/>
メソッドで変更を報告する方法を示すフラグを指定します。 このパラメーターが TRUE の場合、このメソッドは直ちに返され、レポートは、指定されたイベントを通知することによって変更。 このパラメーターが FALSE の場合、変更が発生するまで、メソッドは返しません。 場合*hEvent*有効なイベントで指定されていない、 *bAsync*パラメーターが TRUE にすることはできません。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  このメソッドでは、指定したキーが削除された場合、呼び出し元は通知されません。

詳細およびサンプル プログラムでは、次を参照してください。 [RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue)します。

##  <a name="open"></a>  CRegKey::Open

指定したキーを開き、設定するには、このメソッドを呼び出す[m_hKey](#m_hkey)にこのキーのハンドル。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>パラメーター

*hKeyParent*<br/>
オープンするキーのハンドル。

*lpszKeyName*<br/>
作成または開かれたキーの名前を指定します。 この名前のサブキーである必要があります*hKeyParent*します。

*samDesired*<br/>
キーのセキュリティのアクセス。 既定値は、KEY_ALL_ACCESS です。 使用可能な値と説明の一覧は、次を参照してください。 [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) Windows SDK に含まれています。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS; を返しますそれ以外の場合、0 以外のエラー値は、WINERROR で定義します。H.

### <a name="remarks"></a>Remarks

場合、 *lpszKeyName*パラメーターが NULL またはポイント空の文字列に`Open`によって識別されるキーの新しいハンドルを開いて*hKeyParent*がいずれかの前に開かれたハンドルは閉じません。

異なり[CRegKey::Create](#create)、`Open`が存在しない場合、指定したキーは作成されません。

##  <a name="operator_hkey"></a>  CRegKey::operator HKEY

変換を`CRegKey`HKEY するオブジェクト。

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>  CRegKey::operator =

代入演算子。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
コピーするキー。

### <a name="return-value"></a>戻り値

新しいキーへの参照を返します。

### <a name="remarks"></a>Remarks

この演算子をデタッチします*キー*その現在のオブジェクトからに割り当てます、`CRegKey`オブジェクトの代わりにします。

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

指定された値の名前のバイナリ データを取得するには、このメソッドを呼び出します。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。

*pValue*<br/>
値のデータを受け取るバッファーへのポインター。

*pnBytes*<br/>
バッファーのバイト単位で、サイズを指定する変数へのポインターが指す、 *pValue*パラメーター。 メソッドが戻るときに、この変数には、バッファーにコピーされたデータのサイズが含まれています。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドは、値の読み取りに失敗した場合、WINERROR で定義されている 0 以外のエラー コードを返します。H. 種類が REG_BINARY の参照されるデータがない場合は、定義が返されます。

### <a name="remarks"></a>Remarks

このメソッドを利用`RegQueryValueEx`を正しい種類のデータが返されることを確認します。 参照してください[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)の詳細。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。 また、 [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)このメソッドによって使用される関数が NULL 終端である文字列を明示的に処理しません。 呼び出し元のコードの両方の条件をチェックする必要があります。

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

DWORD データ値を指定した名前を取得するには、このメソッドを呼び出します。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。

*dwValue*<br/>
Dword 値を受け取るバッファーへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドは、値の読み取りに失敗した場合、WINERROR で定義されている 0 以外のエラー コードを返します。H. REG_DWORD 型の参照されるデータがない場合は、定義が返されます。

### <a name="remarks"></a>Remarks

このメソッドを利用`RegQueryValueEx`を正しい種類のデータが返されることを確認します。 参照してください[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)の詳細。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。 また、 [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)このメソッドによって使用される関数が NULL 終端である文字列を明示的に処理しません。 呼び出し元のコードの両方の条件をチェックする必要があります。

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

GUID データ値を指定した名前を取得するには、このメソッドを呼び出します。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。

*guidValue*<br/>
GUID を受け取る変数へのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドは、値の読み取りに失敗した場合、WINERROR で定義されている 0 以外のエラー コードを返します。H. 参照されるデータは、有効な GUID ではありません、定義が返されます。

### <a name="remarks"></a>Remarks

このメソッドを利用`CRegKey::QueryStringValue`GUID を使用して、文字列に変換および[CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring)します。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

指定された値名の複数行文字列のデータを取得するには、このメソッドを呼び出します。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。

*終端*<br/>
複数行文字列のデータを受信するバッファーへのポインター。 複数文字列は、2 つの null 文字で終端の null で終わる文字列の配列です。

*が*<br/>
サイズが指すバッファーの Tchar*終端*します。 メソッドが戻るときに*が*Tchar、終端の null 文字も含めて取得するには、複数のサイズが含まれています。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドは、値の読み取りに失敗した場合、WINERROR で定義されている 0 以外のエラー コードを返します。H. REG_MULTI_SZ 型の参照されるデータがない場合は、定義が返されます。

### <a name="remarks"></a>Remarks

このメソッドを利用`RegQueryValueEx`を正しい種類のデータが返されることを確認します。 参照してください[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)の詳細。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。 また、 [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)このメソッドによって使用される関数が NULL 終端である文字列を明示的に処理しません。 呼び出し元のコードの両方の条件をチェックする必要があります。

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

QWORD データが指定された値の名前を取得するには、このメソッドを呼び出します。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。

*qwValue*<br/>
QWORD を受け取るバッファーへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドは、値の読み取りに失敗した場合、WINERROR で定義されている 0 以外のエラー コードを返します。H. REG_QWORD 型の参照されるデータがない場合は、定義が返されます。

### <a name="remarks"></a>Remarks

このメソッドを利用`RegQueryValueEx`を正しい種類のデータが返されることを確認します。 参照してください[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)の詳細。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。 また、 [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)このメソッドによって使用される関数が NULL 終端である文字列を明示的に処理しません。 呼び出し元のコードの両方の条件をチェックする必要があります。

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

指定された値名の文字列データを取得するには、このメソッドを呼び出します。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。

*終端*<br/>
文字列データを受信するバッファーへのポインター。

*が*<br/>
サイズが指すバッファーの Tchar*終端*します。 メソッドが戻るときに*が*Tchar、終端の null 文字も含めて取得するには、文字列のサイズが含まれています。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドは、値の読み取りに失敗した場合、WINERROR で定義されている 0 以外のエラー コードを返します。H. REG_SZ 型の参照されるデータがない場合は、定義が返されます。 メソッドは、ERROR_MORE_DATA を返す場合*が*が 0、バイト単位で必要なバッファー サイズではなく。

### <a name="remarks"></a>Remarks

このメソッドを利用`RegQueryValueEx`を正しい種類のデータが返されることを確認します。 参照してください[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)の詳細。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。 また、 [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)このメソッドによって使用される関数が NULL 終端である文字列を明示的に処理しません。 呼び出し元のコードの両方の条件をチェックする必要があります。

##  <a name="queryvalue"></a>  CRegKey::QueryValue

指定した値のフィールドのデータを取得するには、このメソッドを呼び出す[m_hKey](#m_hkey)します。 このメソッドの以前のバージョンでは、現在サポートされていませんされ、されずとしてマークされます。

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリに値の名前を含む null で終わる文字列へのポインター。 場合*pszValueName*が NULL または空の文字列""、メソッド型を取得、およびキーのデータの名前のないまたは既定値が存在する場合。

*pdwType*<br/>
指定した値に格納されたデータの種類を示すコードを受け取る変数へのポインター。 *PdwType*型コードが必要ない場合、パラメーターは NULL を指定できます。

*pData*<br/>
値のデータを受け取るバッファーへのポインター。 このパラメーターは、データが必要ない場合、NULL にすることができます。

*pnBytes*<br/>
バッファーのバイト単位で、サイズを指定する変数へのポインターが指す、 *pData*パラメーター。 この変数にコピーされたデータのサイズが含まれています、メソッドが戻るとき*pData します。*

*dwValue*<br/>
値フィールドの数値データ。

*lpszValueName*<br/>
クエリを実行する、値フィールドを指定します。

*szValue*<br/>
値フィールドの文字列データです。

*pdwCount*<br/>
文字列データのサイズ。 サイズには、その値は設定された最初に、 *szValue*バッファー。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS; を返しますそれ以外の場合、0 以外のエラー コードは、WINERROR で定義されています。H.

### <a name="remarks"></a>Remarks

2 つの元のバージョンの`QueryValue`はもはやサポートされておらず、されずとしてマークされます。 これらの形式が使用されている場合、コンパイラは警告を発行します。

残りのメソッドは、RegQueryValueEx を呼び出します。

> [!IMPORTANT]
>  このメソッドは、呼び出し元が信頼できないデータを読み取る可能性がある、レジストリの場所を指定できます。 また、このメソッドによって使用される RegQueryValueEx 関数は NULL 終端である文字列を明示的に処理しません。 呼び出し元のコードの両方の条件をチェックする必要があります。

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

指定したキーをレジストリから削除し、すべてのサブキーを明示的に削除するには、このメソッドを呼び出します。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>パラメーター

*lpszKey*<br/>
削除するキーの名前を指定します。 この名前のサブキーである必要があります[m_hKey](#m_hkey)します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS; を返しますそれ以外の場合、0 以外のエラー値は、WINERROR で定義します。H.

### <a name="remarks"></a>Remarks

キーにサブキーがある場合は、キーを削除するには、このメソッドを呼び出す必要があります。

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

レジストリ キーのバイナリ値を設定するには、このメソッドを呼び出します。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*pValue*<br/>
指定された値の名前で格納されるデータを格納するバッファーへのポインター。

*nBytes*<br/>
によって示される情報のバイト単位でサイズを指定、 *pValue*パラメーター。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドを使用して[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)値をレジストリに書き込みます。

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

レジストリ キーの DWORD 値を設定するには、このメソッドを呼び出します。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*dwValue*<br/>
指定された値の名前を格納する DWORD データ。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドを使用して[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)値をレジストリに書き込みます。

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

レジストリ キーの GUID 値を設定するには、このメソッドを呼び出します。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*guidValue*<br/>
指定された値の名前で格納される GUID への参照。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドを利用`CRegKey::SetStringValue`GUID を使用して文字列に変換および[StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2)します。

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

指定したキーの指定した値のフィールドにデータを格納するには、このメソッドを呼び出します。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*lpszKeyName*<br/>
作成または開かれたキーの名前を指定します。 この名前のサブキーである必要があります[m_hKey](#m_hkey)します。

*lpszValue*<br/>
データを格納するを指定します。 このパラメーターは、NULL 以外である必要があります。

*lpszValueName*<br/>
設定する値のフィールドを指定します。 キーにもこの名前の値のフィールドがまだ存在しない場合は、追加されます。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS; を返しますそれ以外の場合、0 以外のエラー コードは、WINERROR で定義されています。H.

### <a name="remarks"></a>Remarks

作成または開くには、このメソッドを呼び出して、 *lpszKeyName*キーを格納、 *lpszValue*内のデータ、 *lpszValueName*値フィールド。

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

レジストリ キーのセキュリティを設定するには、このメソッドを呼び出します。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>パラメーター

*si*<br/>
設定するセキュリティ記述子のコンポーネントを指定します。 値は、次の値の組み合わせを指定できます。

|[値]|説明|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|キーの随意アクセス制御リスト (DACL) を設定します。 キーに対する WRITE_DAC アクセス許可を持っているか、呼び出し元のプロセスは、オブジェクトの所有者である必要があります。|
|GROUP_SECURITY_INFORMATION|キーのプライマリ グループ セキュリティ識別子 (SID) を設定します。 キーは WRITE_OWNER アクセスが必要または呼び出し元のプロセスは、オブジェクトの所有者である必要があります。|
|OWNER_SECURITY_INFORMATION|キーの所有者の SID を設定します。 キーは WRITE_OWNER アクセスが必要または呼び出し元のプロセスがオブジェクトの所有者であるか、有効になっている SE_TAKE_OWNERSHIP_NAME 権限を持っている必要があります。|
|SACL_SECURITY_INFORMATION|キーのシステム アクセス制御リスト (SACL) を設定します。 ACCESS_SYSTEM_SECURITY アクセス キーが必要です。 このアクセスを取得するための適切が SE_SECURITY_NAME を有効にするには[特権](/windows/desktop/secauthz/privileges)呼び出し元の現在のアクセス トークンで ACCESS_SYSTEM_SECURITY へのアクセスのためのハンドルを開くし、特権を無効にします。|

*psd*<br/>
ポインターを[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)構造を指定したキーに設定するセキュリティ属性を指定します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

キーのセキュリティ属性を設定します。 参照してください[RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity)の詳細。

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

レジストリ キーの複数行文字列の値を設定するには、このメソッドを呼び出します。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*終端*<br/>
指定された値の名前で保存する複数行文字列のデータへのポインター。 複数文字列は、2 つの null 文字で終端の null で終わる文字列の配列です。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドを使用して[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)値をレジストリに書き込みます。

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

レジストリ キーの QWORD 値を設定するには、このメソッドを呼び出します。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*qwValue*<br/>
指定された値の名前で格納される QWORD データ。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドを使用して[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)値をレジストリに書き込みます。

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

レジストリ キーの文字列値を設定します。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*終端*<br/>
指定された値名で格納される文字列データへのポインター。

*dwType*<br/>
レジストリに書き込む文字列の型。REG_SZ (既定値) または REG_EXPAND_SZ (複数文字列の場合)。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドを使用して[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)値をレジストリに書き込みます。

##  <a name="setvalue"></a>  CRegKey::SetValue

指定された値 フィールドのデータを格納するには、このメソッドを呼び出す[m_hKey](#m_hkey)します。 このメソッドの以前のバージョンでは、現在サポートされていませんされ、されずとしてマークされます。

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がキーに存在しないメソッドにより、キーに追加します。 場合*pszValueName*が NULL または空の文字列""の種類を設定する方法、およびキーのデータの名前のないまたは既定値。

*dwType*<br/>
参照するデータの種類を示すコードを指定します、 *pValue*パラメーター。

*pValue*<br/>
指定された値の名前で格納されるデータを格納するバッファーへのポインター。

*nBytes*<br/>
によって示される情報のバイト単位でサイズを指定、 *pValue*パラメーター。 データの型が REG_SZ、REG_EXPAND_SZ、または、REG_MULTI_SZ の場合*nBytes*終端の null 文字のサイズを含める必要があります。

*hKeyParent*<br/>
オープンするキーのハンドル。

*lpszKeyName*<br/>
作成または開かれたキーの名前を指定します。 この名前のサブキーである必要があります*hKeyParent*します。

*lpszValue*<br/>
データを格納するを指定します。 このパラメーターは、NULL 以外である必要があります。

*lpszValueName*<br/>
設定する値のフィールドを指定します。 キーにもこの名前の値のフィールドがまだ存在しない場合は、追加されます。

*dwValue*<br/>
データを格納するを指定します。

*bMulti*<br/>
False の場合は、REG_SZ 型の文字列を示します。 True の場合は、文字列は、REG_MULTI_SZ の種類の複数文字列を示します。

*nValueLen*<br/>
場合*bMulti*が true の場合*nValueLen*の長さ、 *lpszValue*文字列の文字。 場合*bMulti*が false の場合、値-1 は、メソッドの計算で、長さが自動的に処理されますを示します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS; を返しますそれ以外の場合、0 以外のエラー コードは、WINERROR で定義されています。H.

### <a name="remarks"></a>Remarks

2 つの元のバージョンの`SetValue`されずとしてマークされ、使用する必要があります。 これらの形式が使用されている場合、コンパイラは警告を発行します。

3 番目のメソッド呼び出し[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)します。

## <a name="see-also"></a>関連項目

[DCOM のサンプル](../../overview/visual-cpp-samples.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
