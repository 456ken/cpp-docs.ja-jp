---
title: idl_module (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 80e4909a61b5b53ecde19471f2c838dd4c425874
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034979"
---
# <a name="idlmodule"></a>idl_module

.Dll ファイルにエントリ ポイントを指定します。

## <a name="syntax"></a>構文

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>パラメーター

*name*<br/>
.Idl ファイルに表示されるコード ブロックのユーザー定義の名前。

*dllname*<br/>
(省略可能)エクスポートを含む .dll ファイルです。

*uuid*<br/>
(省略可能)一意の id。

*helpstring*<br/>
(省略可能)タイプ ライブラリを記述するために使用する文字の文字列。

*helpstringcontext*<br/>
(省略可能).Hlp や .chm ファイル内のヘルプ トピックの ID。

*helpcontext*<br/>
(省略可能)このタイプ ライブラリのヘルプ ID です。

*hidden*<br/>
(省略可能)ライブラリが表示されないようにするパラメーター。 詳細については、「 [hidden](/windows/desktop/Midl/hidden) 」の MIDL 属性に関する説明を参照してください。

*restricted*<br/>
(省略可能)ライブラリのメンバーは任意に呼び出すことができません。 詳細については、「 [restricted](/windows/desktop/Midl/restricted) 」の MIDL 属性に関する説明を参照してください。

*関数の宣言*<br/>
この関数を定義します。

## <a name="remarks"></a>Remarks

**Idl_module** C++属性を使用して、.dll ファイルからインポートすることができる .dll ファイルにエントリ ポイントを指定できます。

**Idl_module**属性と同様の機能を持つ、[モジュール](/windows/desktop/Midl/module)MIDL 属性。

.Idl ファイルのライブラリ ブロックに DLL のエントリ ポイントを配置することで、.dll ファイルからエクスポートできる COM オブジェクトから何もエクスポートできます。

使用する必要があります**idl_module**で 2 つの手順。 最初に、名前または DLL のペアを定義する必要があります。 次に、使用**idl_module**エントリ ポイントを指定する名前と追加の属性を指定します。

## <a name="example"></a>例

次のコードを使用する方法を示しています、 **idl_module**属性。

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|任意の場所|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)<br/>
[entry](entry.md)