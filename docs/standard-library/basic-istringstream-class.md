---
title: basic_istringstream クラス
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: fdf622bbef370e8b3625f419be29f293bc06eacc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400631"
---
# <a name="basicistringstream-class"></a>basic_istringstream クラス

クラス [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> のストリーム バッファーからの、要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>パラメーター

*Alloc*<br/>
アロケーター クラス。

*Elem*<br/>
文字列の基本要素の型。

*Tr*<br/>
文字列の基本要素に特化した文字の特徴。

## <a name="remarks"></a>Remarks

テンプレート クラスは、クラスのストリーム バッファーからエンコードされたオブジェクトと要素の抽出を制御するオブジェクトについて説明します[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**、 **Tr。**、 `Alloc`>、型の要素を含む*Elem*、その文字特性はクラスによって決まります*Tr*、クラスのアロケーターによって割り当てられている要素と*Alloc*します。 このオブジェクトは、クラス basic_stringbuf< **Elem**, **Tr**, `Alloc`> のオブジェクトを格納します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_istringstream](#basic_istringstream)|`basic_istringstream` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[allocator_type](#allocator_type)|この型は、テンプレート パラメーター `Alloc` のシノニムです。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[rdbuf](#rdbuf)|型 `pointer` の格納されたストリーム バッファーのアドレスを [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> に返します。|
|[str](#str)|文字列バッファー内のテキストを設定または取得します。書き込み位置は変更しません。|
|[swap](#swap)|この `basic_istringstream` オブジェクト内の値を、提供されるオブジェクトの値と交換します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|オブジェクト パラメーターの値をこの `basic_istringstream` オブジェクトに代入します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<sstream>

**名前空間:** std

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

この型は、テンプレート パラメーター `Alloc` のシノニムです。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

`basic_istringstream` 型のオブジェクトを構築します。

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>パラメーター

*_Mode*<br/>
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) の列挙値のうちの 1 つ。

*str*<br/>
`basic_string` 型のオブジェクト。

*right*<br/>
`basic_istringstream` オブジェクトの右辺値参照。

### <a name="remarks"></a>Remarks

最初のコンス トラクターを呼び出して基底クラスを初期化する[basic_istream](../standard-library/basic-istream-class.md)(`sb`) ここで、`sb`クラスの格納されているオブジェクトは、 [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`、 `Tr`、 `Alloc`>。 また、`basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`) を呼び出すことで `sb` の初期化もします。

2 番目のコンストラクターが `basic_istream(sb)` を呼び出して基底クラスを初期化します。 また、`basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`) を呼び出すことで `sb` の初期化もします。

3 番目のコンス トラクターによって初期化の内容を持つオブジェクト*右*、右辺値参照として扱われます。

## <a name="op_eq"></a>  basic_istringstream::operator=

オブジェクト パラメーターの値をこの `basic_istringstream` オブジェクトに代入します。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
`basic_istringstream` オブジェクトへの右辺値参照。

### <a name="remarks"></a>Remarks

メンバー演算子は、オブジェクトの内容の内容に置き換えます*右*右辺値参照の移動代入として処理され、します。

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

型の格納されたストリーム バッファーのアドレスを返して`pointer`に[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**、 **Tr**、 `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>戻り値

型の格納されたストリーム バッファーのアドレス`pointer`basic_stringbuf < **Elem**、 **Tr**、 `Alloc`>。

### <a name="example"></a>例

`rdbuf` の使用例については、「[basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)」を参照してください。

## <a name="str"></a>  basic_istringstream::str

文字列バッファー内のテキストを設定または取得します。書き込み位置は変更しません。

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>パラメーター

*_Newstr*<br/>
新しい文字列。

### <a name="return-value"></a>戻り値

制御されたシーケンスが **\*this** によって制御されるシーケンスのコピーである、クラス [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> のオブジェクトを返します。

### <a name="remarks"></a>Remarks

最初のメンバー関数は [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str) を返します。 2 番目のメンバー関数は `rdbuf` -> **str**( `_Newstr`) を呼び出します。

### <a name="example"></a>例

参照してください[basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str)を使用する例については`str`します。

## <a name="swap"></a>  basic_istringstream::swap

2 つの `basic_istringstream` オブジェクトの値を交換します。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*right*|`basic_istringstream` オブジェクトへの `lvalue` 参照。|

### <a name="remarks"></a>Remarks

メンバー関数は、このオブジェクトの値との値を交換する*右*します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream プログラミング](../standard-library/iostream-programming.md)<br/>
[iostreams の規則](../standard-library/iostreams-conventions.md)<br/>
