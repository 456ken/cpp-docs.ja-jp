---
title: 列挙型クラス (C +/cli および C++/cli CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: aee3d4f44c18074ca536ff028565bbbd0e37d04c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417425"
---
# <a name="enum-class--ccli-and-ccx"></a>列挙型クラス (C +/cli および C++/cli CX)

名前空間スコープで列挙型を宣言します。列挙型とは、列挙子と呼ばれる一連の名前付き定数で構成されるユーザー定義型です。

## <a name="all-runtimes"></a>すべてのランタイム

### <a name="remarks"></a>Remarks

C +/cli/CX および C++/cli サポート**パブリック列挙型クラス**と**プライベート列挙型クラス**は標準の C++ のような**列挙型クラス**がユーザー補助機能の追加指定子。 **/Clr**、c++ 11**列挙型クラス**型が許可されているが、本当に ISO の列挙型としない、C + することを確認するためのものが警告 C4472 が生成されます/cli/CX および C++/cli CLI 型。 ISO 標準の C++ の詳細については**enum**キーワードを参照してください[列挙](../cpp/enumerations-cpp.md)します。

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="syntax"></a>構文

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>パラメーター

*access*<br/>
列挙型のアクセシビリティ**パブリック**または**プライベート**します。

*enumeration-identifier*<br/>
列挙型の名前。

*underlying-type*<br/>
(省略可能) 列挙型の基になる型。

(省略可能、 Windows ランタイムのみ) は、列挙体の基になる型**bool**、 **char**、 `char16`、 `int16`、 `uint16`、 **int**、 `uint32`、 `int64`、または`uint64`します。

*enumerator-list*<br/>
列挙子名のコンマ区切りのリスト。

それぞれの列挙子の値は、コンパイラによって暗黙的に定義された定数式か、" *enumerator*`=`*constant-expression*」をご覧ください。 既定では、最初の列挙子が暗黙的に定義されている場合、その値は 0 です。 それ以降の暗黙的に定義された列挙子の値は、前の列挙子の値に 1 を加算した値になります。

*var*<br/>
(省略可能) 列挙型の変数の名前。

### <a name="remarks"></a>Remarks

使用例を含む詳細については、「 [列挙型](../cppcx/enums-c-cx.md)」をご覧ください。

列挙子の値を定義する定数式が *underlying-type*で表すことができない場合、コンパイラはエラー メッセージを生成します。  ただし、基になる型に対して値が不適切であるというエラーは生成されません。 例:

- *underlying-type* が数値であり、列挙子がその型の最大値を指定する場合は、次に暗黙的に定義されている列挙型の値は表すことができません。

- 場合*基になる型*は**bool**、3 つ以上の列挙子が暗黙的には、最初の 2 つを表すことができない後の列挙を定義します。

- *underlying-type* が `char16`であり、列挙型の値が 0xD800 から 0xDFFF の範囲にある場合、その値を表すことができます。 この値は Unicode サロゲート ペアの一方を表していますが、このペアは分離して表すことができないため、論理的にはこの値は正しくありません。

### <a name="requirements"></a>必要条件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="syntax"></a>構文

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>パラメーター

*access*<br/>
列挙型のアクセシビリティ。 いずれかになります**パブリック**または**プライベート**します。

*enumerator-list*<br/>
列挙型に含まれる識別子 (列挙子) のコンマ区切りのリスト。

*name*<br/>
列挙型の名前。 匿名のマネージド列挙型は使用できません。

*type*<br/>
(省略可能)基になる型、*識別子*します。 符号付きまたは符号なしのバージョンなどの任意のスカラー型を指定できます**int**、**短い**、または**長い**します。  **bool**または**char**も使用できます。

*var*<br/>
(省略可能) 列挙型の変数の名前。

### <a name="remarks"></a>Remarks

**enum class** と **enum struct** は同等の宣言です。

列挙型には、マネージド (C++/CX) 列挙型と標準列挙型の 2 種類があります。

マネージド (C++/CX) 列挙型は、たとえば次のように定義されます。

```cpp
public enum class day {sun, mon };
```

これは、次のコードと同じ意味です。

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

標準列挙型は、たとえば次のように定義されます。

```cpp
enum day2 { sun, mon };
```

これは、次のコードと同じ意味です。

```cpp
static const int sun = 0;
static const int mon = 1;
```

マネージド列挙子の名前 (*識別子*) は、列挙型が定義されるスコープに挿入されません。列挙子へのすべての参照が完全修飾名であることが必要です (*名前*`::`*識別子*)。  そのため、匿名のマネージド列挙型は定義できません。

標準列挙型の列挙子は外側のスコープに厳密に挿入されます。  そのため、列挙子と同じ名前を持つ別のシンボルが外側のスコープにある場合、コンパイラはエラーを生成します。

Visual Studio 2002 および Visual Studio 2003 で列挙子は弱く挿入されて (表示されている外側のスコープ内に同じ名前の別の識別子がない)。

C++ 標準列挙型が定義されている場合 (せず**クラス**または**構造体**) を指定してコンパイル、`/clr`マネージ列挙型としてコンパイルする列挙型になります。  この列挙型のセマンティクスはアンマネージ列挙型のままです。  ただし、コンパイラは、属性を挿入`Microsoft::VisualC::NativeEnumAttribute`ネイティブ列挙型を指定する列挙型のプログラマの意図を識別するためにします。  他のコンパイラは、標準列挙型を単にマネージド列挙型として認識します。

A という名前で、標準列挙型がコンパイルされた`/clr`マネージ列挙型としてアセンブリに表示されますおよびその他の任意のマネージ コンパイラで使用できます。   ただし、名前のない標準列挙体は、アセンブリからパブリックに参照することができません。

Visual Studio 2002 および Visual Studio 2003 では、標準列挙型は関数のパラメーター型として使用します。

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

これは、関数のシグネチャに対応して MSIL に次の出力を行います。

```cpp
void f(int32);
```

ただし、現在のバージョンのコンパイラでは、[NativeEnumAttribute] を指定すると標準列挙型がマネージド列挙型として出力され、関数のシグネチャに対応して MSIL に次の出力を行います。

```cpp
void f(E)
```

ネイティブ列挙型の詳細については、「 [C++ 列挙体の宣言](../cpp/enumerations-cpp.md)」を参照してください。

CLR 列挙型の詳細については、次のページを参照してください。

- [Underlying Type of an Enum (列挙型の基になる型)](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>必要条件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](../windows/component-extensions-for-runtime-platforms.md)