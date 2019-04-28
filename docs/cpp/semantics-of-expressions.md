---
title: 式のセマンティクス
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: d2ce510478bcf1574429c85f704552e6b73100ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331214"
---
# <a name="semantics-of-expressions"></a>式のセマンティクス

式は、式の演算子の優先順位とグループ化に従って評価されます ([演算子の優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)で[構文規則](../cpp/lexical-conventions.md)演算子が式を課す、C++ の関係を示しています)。

## <a name="order-of-evaluation"></a>評価の順序

次の例について考えます。

```cpp
// Order_of_Evaluation.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main()
{
    int a = 2, b = 4, c = 9;

    cout << a + b * c << "\n";
    cout << a + (b * c) << "\n";
    cout << (a + b) * c << "\n";
}
```

```Output
38
38
54
```

![式の評価順序](../cpp/media/vc38zv1.gif "式の評価順序") <br/>
式の評価順序

上の図に示す式が評価される順序は、演算子の優先順位と結合規則によって決まります。

1. この式では、乗算 (*) が最も高い優先順位を持ちます。したがって、部分式 `b * c` が最初に評価されます。

1. 次に優先順位が高いのは加算 (+) であるため、`a` と `b` の積に `c` が加算されます。

1. 左シフト (<<) の式で最低の優先順位を持つが、2 つのアイテムがあります。 左シフト演算子は左から右にグループ化されるため、左の部分式が最初に評価され、次に右の部分式が評価されます。

かっこを使用して部分式がグループ化されている場合は、優先順位が変更されるため、次の図に示すように、式の評価順序も変更されます。

![かっこ付きの式の評価順序](../cpp/media/vc38zv2.gif "かっこ付きの式の評価順序") <br/>
かっこで式の評価順序

上の図のような式は、純粋に式の副作用 (この場合は標準出力デバイスへの情報転送) のためだけに評価されます。

## <a name="notation-in-expressions"></a>式の表記

C++ 言語では、オペランドを指定するときに、特定の互換性を指定します。 次の表は型のオペランドを必要とする演算子をオペランドの型を指定できる*型*します。

### <a name="operand-types-acceptable-to-operators"></a>演算子に適切なオペランドの型

|想定される型|許可される型|
|-------------------|-------------------|
|*type*|`const` *type*<br /> `volatile` *type*<br /> *type*&<br /> `const` *type*&<br /> `volatile` *type*&<br /> `volatile const` *type*<br /> `volatile const` *type*&|
|*type* \*|*type* \*<br /> `const` *type* \*<br /> `volatile` *type* \*<br /> `volatile const` *type* \*|
|`const` *type*|*type*<br /> `const` *type*<br />`const` *type*&|
|`volatile` *type*|*type*<br /> `volatile` *type*<br /> `volatile` *type*&|

前の規則はいつでも組み合わせて使用できるため、volatile オブジェクトへの const ポインターは、ポインターが想定される場所で指定できます。

## <a name="ambiguous-expressions"></a>あいまいな式

状況によっては、式の意味があいまいになる場合があります。 通常、オブジェクトの値が同じ式で複数回変更されると、このような式が発生します。 これらの式は、評価の特定の順序に依存します (言語が定義しない場合)。 次に例を示します。

```
int i = 7;

func( i, ++i );
```

C++ 言語では、関数呼び出しの引数が評価される順序は保証されません。 したがって、前の例では、左から右、右から左のどちらの方向でパラメーターが評価されるかに応じて、`func` はパラメーターとして値 7 と 8、または 8 と 8 を受け取ります。

## <a name="c-sequence-points-microsoft-specific"></a>C++ シーケンス ポイント (Microsoft 固有の仕様)

式では、連続する "シーケンス ポイント" 間で、オブジェクトの値を一度だけ変更できます。

C++ 言語の定義では、現在シーケンス ポイントは指定されていません。 Microsoft C++ では、C の演算子を伴い、オーバーロードされた演算子を伴わないすべての式に、ANSI C と同じシーケンス ポイントを使用します。 演算子がオーバーロードされている場合、セマンティクスは演算子のシーケンスから関数呼び出しのシーケンスに変更されます。 Microsoft C++ は、次のシーケンス ポイントを使用します。

- 論理 AND 演算子のオペランドを左 ((& a) (& a))。 論理 AND 演算子の左オペランドは完全に評価され、すべての副作用は続行の前に完了します。 論理 AND 演算子の右オペランドが評価される保証はありません。

- 論理 OR 演算子のオペランドを左 (&#124;&#124;)。 論理 OR 演算子の左オペランドは完全に評価され、すべての副作用は続行の前に完了します。 論理 OR 演算子の右オペランドが評価される保証はありません。

- コンマ演算子の左オペランド。 コンマ演算子の左オペランドは完全に評価され、すべての副作用は続行の前に完了します。 コンマ演算子のオペランドは両方とも、常に評価されます。

- 関数呼び出し演算子。 関数呼び出し式と、関数の既定の引数も含めたすべての引数は、評価され、すべての副作用は関数に入る前に完了します。 引数や関数呼び出し式の間に、指定された評価順序はありません。

- 条件演算子の最初のオペランド。 条件演算子の最初のオペランドは完全に評価され、すべての副作用は続行の前に完了します。

- 初期化式全体の最後 (宣言ステートメントでの初期化終了時など)。

- 式ステートメント内の式。 式ステートメントは、省略可能な式とそれに続くセミコロン (;) で構成されます。 式の副作用は完全に評価されます。

- 選択 (if または switch) ステートメント内の制御式。 式は完全に評価され、すべての副作用は選択に依存するコードが実行される前に完了します。

- while または do ステートメントの制御式。 式は完全に評価され、すべての副作用は while または do ループの次のイテレーションのステートメントが実行される前に完了します。

- for ステートメントの 3 つの各式。 各式は完全に評価され、すべての副作用は次の式に移動する前に完了します。

- return ステートメント内の式。 式は完全に評価され、すべての副作用は呼び出し元の関数に制御が戻る前に完了します。

## <a name="see-also"></a>関連項目

[式](../cpp/expressions-cpp.md)