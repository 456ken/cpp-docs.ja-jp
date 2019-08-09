---
title: istreambuf_iterator クラス
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 0a2bbc69d4f2d3af0ee6e00a2672436a5f15ab67
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448124"
---
# <a name="istreambufiterator-class"></a>istreambuf_iterator クラス

istreambuf_iterator テンプレート クラスは、入力ストリーム バッファーから文字要素を抽出する入力反復子オブジェクトを表します。これには、`basic_streambuf`\< **CharType**, **Traits**> へのポインター型の、格納されたオブジェクトを介してアクセスします。

## <a name="syntax"></a>構文

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>パラメーター

*CharType*\
istreambuf_iterator の文字型を表す型。

*名札*\
istreambuf_iterator の文字型を表す型。 この引数は省略可能であり、既定値は `char_traits`\< *CharType>* です。

## <a name="remarks"></a>Remarks

istreambuf_iterator クラスは入力反復子の要件を満たす必要があります。

null 以外の格納されたポインターを使用して istreambuf_iterator クラスのオブジェクトを構築またはインクリメントすると、オブジェクトは、関連付けられている入力ストリームから *CharType* 型のオブジェクトを効果的に抽出および格納することを試行します。 ただし、抽出はオブジェクトが実際に逆参照またはコピーされるまで遅延することがあります。 抽出が失敗した場合、オブジェクトは効果的に格納されたポインターを null ポインターに置き換え、シーケンス終端のインジケーターを作成します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|入力ストリームから文字を読み取るために初期化される `istreambuf_iterator` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|`ostreambuf_iterator` の文字型を提供する型。|
|[int_type](#int_type)|`istreambuf_iterator` の整数型を提供する型。|
|[istream_type](#istream_type)|`istream_iterator` のストリーム型を提供する型。|
|[streambuf_type](#streambuf_type)|`istreambuf_iterator` のストリーム型を提供する型。|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|`istream_iterator` の文字特性型を提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[equal](#equal)|2 つ入力ストリーム バッファー反復子の等価性をテストします。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator*](#op_star)|逆参照演算子は、ストリーム内の次の文字を返します。|
|[operator++](#op_add_add)|入力ストリームから次の文字を返すか、オブジェクトをインクリメントする前にオブジェクトをコピーして、そのコピーを返します。|
|[operator->](#op_arrow)|メンバーの値 (存在する場合) を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<iterator>

**名前空間:** std

## <a name="char_type"></a>  istreambuf_iterator::char_type

`ostreambuf_iterator` の文字型を提供する型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター *CharType* のシノニムです。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="equal"></a>  istreambuf_iterator::equal

2 つの入力ストリーム バッファー反復子の等価性をテストします。

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
等価性をチェックする反復子。

### <a name="return-value"></a>戻り値

両方の `istreambuf_iterator` がストリームの終わりの反復子であるか、どちらもストリームの終わりの反復子でない場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

範囲は、によって`istreambuf_iterator`現在の位置とストリームの末尾の反復子によって定義されますが、すべての非終端ストリーム反復子が`equal`メンバー関数の下で等価であるため、を使用`istreambuf_iterator`して部分範囲を定義することはできません。 `==` 演算子と `!=` 演算子は同じセマンティクスを持ちます。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="int_type"></a>  istreambuf_iterator::int_type

`istreambuf_iterator` の整数型を提供する型。

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Remarks

この型は `Traits::int_type` の同意語です。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istream_type"></a>  istreambuf_iterator::istream_type

`istreambuf_iterator` のストリーム型を提供する型。

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Remarks

この型は、`basic_istream`\< **CharType**, **Traits**> のシノニムです。

### <a name="example"></a>例

`istream_type` を宣言して使用する方法の例については、[istreambuf_iterator](#istreambuf_iterator) に関するセクションをご覧ください。

## <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator

入力ストリームから文字を読み取るために初期化される istreambuf_iterator を構築します。

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>パラメーター

*strbuf*\
`istreambuf_iterator` が関連付けられている入力ストリーム バッファー。

*_Istr*\
`istreambuf_iterator` が関連付けられている入力ストリーム。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、 *strbuf*で入力ストリームバッファーポインターを初期化します。 2番目のコンストラクターは、 *_Istr*を使用して入力ストリームバッファーポインターを初期化します。 `rdbuf`次に、は、型`CharType`のオブジェクトの抽出と格納を試みます。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="op_star"></a>  istreambuf_iterator::operator*

逆参照演算子は、ストリーム内の次の文字を返します。

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>戻り値

ストリーム内の次の文字。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="op_add_add"></a>  istreambuf_iterator::operator++

入力ストリームから次の文字を返すか、オブジェクトをインクリメントする前にオブジェクトをコピーして、そのコピーを返します。

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>戻り値

`istreambuf_iterator` または、`istreambuf_iterator` への参照。

### <a name="remarks"></a>Remarks

最初の演算子は、最終的に、関連付けられて`CharType`いる入力ストリームから型のオブジェクトの抽出と格納を試みます。 2 つ目の演算子は、オブジェクトのコピーを作成して、オブジェクトをインクリメントしてから、そのコピーを返します。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="op_arrow"></a>  istreambuf_iterator::operator-&gt;

メンバーの値 (存在する場合) を返します。

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>戻り値

この演算子は、 **&\*\*this** を返します。

## <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type

istreambuf_iterator のストリーム型を提供する型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Remarks

この型は、`basic_streambuf`\< **CharType**, **Traits**> のシノニムです。

### <a name="example"></a>例

`istreambuf_type` を宣言して使用する方法の例については、[istreambuf_iterator](#istreambuf_iterator) に関するセクションをご覧ください。

## <a name="traits_type"></a>  istreambuf_iterator::traits_type

`istream_iterator` の文字特性型を提供する型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター *Traits* のシノニムです。

### <a name="example"></a>例

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>関連項目

[iterator 構造体](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
