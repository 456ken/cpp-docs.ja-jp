---
title: pair 構造体
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: 2b7f2b736d24961376db4317d6d53e06153283c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370646"
---
# <a name="pair-structure"></a>pair 構造体

2 つのオブジェクトを 1 つのオブジェクトとして処理する機能を提供する構造体。

## <a name="syntax"></a>構文

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);
};
```

### <a name="parameters"></a>パラメーター

*Val1*<br/>
`pair` の最初の要素を初期化する値。

*Val2*<br/>
`pair` の 2 番目の要素を初期化する値。

*右*<br/>
別のペアの要素を初期化するために値が使用されるペア。

## <a name="return-value"></a>戻り値

(既定値) の最初のコンス トラクターが型の既定値のペアの最初の要素を初期化します`T1`と 2 番目の要素型の既定値に`T2`します。

2 番目のコンス トラクターがペアの最初の要素を初期化します*Val1*し、2 番目*Val2 です。*

3 番目の (テンプレート) コンストラクターは、ペアの最初の要素を `Right`. **first** および 2 つ目の要素を `Right`. **second**。

4 番目のコンス トラクターがペアの最初の要素を初期化します*Val1*し、2 番目*Val2*を使用して[右辺値参照宣言子: & &](../cpp/rvalue-reference-declarator-amp-amp.md)します。

## <a name="remarks"></a>Remarks

テンプレート構造体の型のオブジェクトのペアを格納する`T1`と`T2`、それぞれします。 型`first_type`はテンプレート パラメーターと同じ`T1`と種類`second_type`はテンプレート パラメーターと同じ`T2`します。 `T1` `T2`それぞれ既定のコンス トラクターにのみ、引数が 1 つのコンス トラクター、およびデストラクターを指定する必要があります。 `pair` 型は**クラス**としてではなく `struct` として宣言されているため、この型のメンバーはすべてパブリックです。 ペアの最も一般的な用途としては、2 つの値を返す関数の戻り値の型としての用途と、連想コンテナー クラスの [map クラス](../standard-library/map-class.md)と [multimap クラス](../standard-library/multimap-class.md)の要素としての用途の 2 つが挙げられます。これらのクラスはどちらも、キーと、各要素に関連付けられている値の型を持っています。 後者は、ペアの連想コンテナーの要件を満たしており、`pair`< **const**`key_type`, `mapped_type`> 形式の値の型を持っています。

## <a name="example"></a>例

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
/* Output:
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
*/
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<utility>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
