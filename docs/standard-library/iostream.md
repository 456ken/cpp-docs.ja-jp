---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 471b149eba32d163e6e3e54e1c2820bbe0b94133
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449038"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

標準ストリームに対する読み取りと書き込みを制御するオブジェクトを宣言します。 多くの場合、このインクルードは、 C++プログラムから入力と出力を行うために必要な唯一のヘッダーです。

## <a name="syntax"></a>構文

```cpp
#include <iostream>
```

> [!NOTE]
> Iostream \<> ライブラリは、 `#include <ios>` `#include <streambuf>` `#include <ostream>` 、、、およびの各ステートメントを使用します。 `#include <istream>`

## <a name="remarks"></a>Remarks

このオブジェクトは、次の 2 つのグループに分類されます。

- [cin](#cin)、 [cout](#cout)、 [cerr](#cerr) [、および](#clog)はバイト指向で、従来のバイト単位の転送を実行します。

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr)、および [wclog](#wclog) はワイド指向で、プログラムが内部で操作するワイド文字に翻訳したり、ワイド文字から翻訳したりします。

標準入力など、ストリームに対して特定の操作を実行すると、同じストリームで別の向きの操作を行うことはできません。 そのため、 [cin](#cin)と[wcin](#wcin)の両方で、プログラムを同じように操作することはできません。

このヘッダーで宣言されたすべてのオブジェクトは、特別なプロパティを共有します。これは、定義するすべての静的なオブジェクト\<の前に、iostream > を含む翻訳単位で構築されていることを前提としています。 同様に、定義した静的オブジェクトのデストラクターの前に、これらのオブジェクトが破棄されないと見なすことができます。 (ただし、出力ストリームはプログラムの終了時にフラッシュされます)。そのため、プログラムの開始前とプログラムの終了後に、標準ストリームに対する安全な読み取りまたは書き込みを行うことができます。

ただし、この保証は一般的ではありません。 静的コンストラクターは、別の翻訳単位で、関数を呼び出す場合があります。 呼び出された関数は、このヘッダーで宣言されたオブジェクトが構築されていると想定できません。これは、静的な構築に含まれる翻訳単位の順序が不明であることを前提としています。 このようなコンテキストでこれらのオブジェクトを使用するには、最初に [ios_base::Init](../standard-library/ios-base-class.md#init) クラスのオブジェクトを構築します。

### <a name="global-stream-objects"></a>グローバル ストリーム オブジェクト

|||
|-|-|
|[cerr](#cerr)|`cerr` グローバル ストリームを指定します。|
|[cin](#cin)|`cin` グローバル ストリームを指定します。|
|[clog](#clog)|`clog` グローバル ストリームを指定します。|
|[cout](#cout)|`cout` グローバル ストリームを指定します。|
|[wcerr](#wcerr)|`wcerr` グローバル ストリームを指定します。|
|[wcin](#wcin)|`wcin` グローバル ストリームを指定します。|
|[wclog](#wclog)|`wclog` グローバル ストリームを指定します。|
|[wcout](#wcout)|`wcout` グローバル ストリームを指定します。|

###  <a name="cerr"></a>cerr

オブジェクト `cerr` は、\<cstdio> で宣言されたオブジェクト `stderr` に関連付けられているストリーム バッファーへの出力を制御します。

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>戻り値

[ostream](../standard-library/ostream-typedefs.md#ostream) オブジェクト。

#### <a name="remarks"></a>Remarks

このオブジェクトは、バイト ストリームとして、標準エラー出力へのバッファリングされていない挿入を制御します。 オブジェクトが構築された時点で、式 `cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) は 0 以外で、`cerr.tie() == &cout` になります。

#### <a name="example"></a>例

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

###  <a name="cin"></a>cin

`cin` グローバル ストリームを指定します。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>戻り値

[istream](../standard-library/istream-typedefs.md#istream) オブジェクト。

#### <a name="remarks"></a>Remarks

オブジェクトは、バイト ストリームとして標準入力からの抽出を制御します。 オブジェクトが構築されると、`cin.`[tie](../standard-library/basic-ios-class.md#tie) の呼び出しは `&`[cout](#cout) を返します。

#### <a name="example"></a>例

この例では`cin` 、は、数値以外の文字が含まれている場合に、ストリームの fail ビットを設定します。 プログラムは、fail ビットをクリアし、ストリームから無効な文字を除去して続行します。

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

###  <a name="clog"></a>clog

`clog` グローバル ストリームを指定します。

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>戻り値

[ostream](../standard-library/ostream-typedefs.md#ostream) オブジェクト。

#### <a name="remarks"></a>Remarks

このオブジェクトは、バイト ストリームとして、標準エラー出力へのバッファリングされている挿入を制御します。

#### <a name="example"></a>例

`clog` の使用例については、「[cerr](#cerr)」をご覧ください。

###  <a name="cout"></a>cout

`cout` グローバル ストリームを指定します。

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>戻り値

[ostream](../standard-library/ostream-typedefs.md#ostream) オブジェクト。

#### <a name="remarks"></a>Remarks

このオブジェクトは、バイト ストリームとして、標準出力への挿入を制御します。

#### <a name="example"></a>例

`cout` の使用例については、「[cerr](#cerr)」をご覧ください。

### <a name="wcerr"></a>wcerr

`wcerr` グローバル ストリームを指定します。

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>戻り値

[wostream](../standard-library/ostream-typedefs.md#wostream) オブジェクト。

#### <a name="remarks"></a>Remarks

このオブジェクトは、ワイド ストリームとして、標準エラー出力へのバッファリングされていない挿入を制御します。 オブジェクトが構築された時点で、式 `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) は 0 以外になります。

#### <a name="example"></a>例

`wcerr` の使用例については、「[cerr](#cerr)」をご覧ください。

### <a name="wcin"></a>wcin

`wcin` グローバル ストリームを指定します。

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>戻り値

[wistream](../standard-library/istream-typedefs.md#wistream) オブジェクト。

#### <a name="remarks"></a>Remarks

オブジェクトは、ワイド ストリームとして標準入力からの抽出を制御します。 オブジェクトが構築されると、`wcin.`[tie](../standard-library/basic-ios-class.md#tie) の呼び出しは `&`[wcout](#wcout) を返します。

#### <a name="example"></a>例

`wcin` の使用例については、「[cerr](#cerr)」をご覧ください。

### <a name="wclog"></a>wclog

`wclog` グローバル ストリームを指定します。

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>戻り値

[wostream](../standard-library/ostream-typedefs.md#wostream) オブジェクト。

#### <a name="remarks"></a>Remarks

このオブジェクトは、ワイド ストリームとして、標準エラー出力へのバッファリングされている挿入を制御します。

#### <a name="example"></a>例

`wclog` の使用例については、「[cerr](#cerr)」をご覧ください。

### <a name="wcout"></a>wcout

`wcout` グローバル ストリームを指定します。

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>戻り値

[wostream](../standard-library/ostream-typedefs.md#wostream) オブジェクト。

#### <a name="remarks"></a>Remarks

このオブジェクトは、ワイド ストリームとして、標準出力への挿入を制御します。

#### <a name="example"></a>例

`wcout` の使用例については、「[cerr](#cerr)」をご覧ください。

`wcout` ステートメントの `CString` インスタンスは、次の例に示されているように `const wchar_t*` にキャストする必要があります。

```
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

詳細については、「[CString の基本操作](../atl-mfc-shared/basic-cstring-operations.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
