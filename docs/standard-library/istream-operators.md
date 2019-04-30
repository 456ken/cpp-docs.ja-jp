---
title: '&lt;istream&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 05b10c27d8e0cf4c0300bb307d8b7ceda43ddb2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413308"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 演算子

## <a name="op_gt_gt"></a>  演算子&gt;&gt;

ストリームから文字と文字列を抽出します。

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>パラメーター

*ch*<br/>
単一の文字。

*Istr*<br/>
ストリーム。

*str*<br/>
文字列。

*val*<br/>
型。

### <a name="return-value"></a>戻り値

ストリーム

### <a name="remarks"></a>Remarks

`basic_istream` クラスもいくつかの抽出演算子を定義します。 詳細については、「[basic_istream::operator >>](../standard-library/basic-istream-class.md#op_gt_gt)」を参照してください。

下記のテンプレート関数は

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

最大で *N* - 1 の要素を抽出し、_ *Str* から始まる配列にこれらを格納します。 `Istr`. [width](../standard-library/ios-base-class.md#width) が 0 より大きい場合、*N* は `Istr`. **幅**。 それ以外の最大の配列のサイズが`Elem`を宣言することができます。 関数は常に値を格納`Elem()`後、抽出された要素が格納されます。 抽出は、ファイルの最後の早い段階で、値 **Elem**(0) (これは抽出されません) を持つ文字、または [ws](../standard-library/istream-functions.md#ws) によって破棄される任意の要素 (これは抽出されません) で停止します。 関数が要素を抽出しなかった場合、`Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 いずれの場合も、`Istr`. **幅**(0) を返します*Istr*します。

**セキュリティに関する注意**入力ストリームから抽出される null で終わる文字列がコピー先のバッファーのサイズを超えない*str*します。 詳しくは、「 [バッファー オーバーランの回避](/windows/desktop/SecBP/avoiding-buffer-overruns)」をご覧ください。

下記のテンプレート関数は

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

格納し、可能であれば場合、に、要素を抽出します*Ch*します。 そうでない場合は、**is**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**) を呼び出します。 いずれのケースを返します*Istr*します。

下記のテンプレート関数は

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

`Istr >> ( char * ) str` が返されます。

下記のテンプレート関数は

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

`Istr >> ( char& ) Ch` が返されます。

下記のテンプレート関数は

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

`Istr >> ( char * ) str` が返されます。

下記のテンプレート関数は

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

`Istr >> ( char& ) Ch` が返されます。

下記のテンプレート関数は

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

返します`Istr >> val`(への右辺値参照に変換します`Istr`プロセスでは左辺値へ)。

### <a name="example"></a>例

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>関連項目

[\<istream>](../standard-library/istream.md)<br/>
