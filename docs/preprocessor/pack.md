---
title: pack プラグマ
ms.date: 08/29/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 4bf0b3d4529de012f4a09d6e60a5b112b9a101df
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218754"
---
# <a name="pack-pragma"></a>pack プラグマ

構造体、共用体、およびクラスメンバーのパッキングアラインメントを指定します。

## <a name="syntax"></a>構文

> **#pragma パック (表示)** \
> **#pragma pack (プッシュ**[ **、** *識別子*] [ **,** *n* ] **)** \
> **#pragma pack (pop** [ **,** { *identifier* | *n* }] **)** \
> **#pragma パック (** [ *n* ] **)**

### <a name="parameters"></a>パラメーター

**示**\
Optionalパッキングアラインメントの現在のバイト値を表示します。 値は警告メッセージによって表示されます。

**押し付け**\
Optional現在のパッキングアラインメント値を内部コンパイラスタックにプッシュし、現在のパッキングアラインメント値を*n*に設定します。 *N*が指定されていない場合、現在のパッキングアラインメント値がプッシュされます。

**ショート**\
Optional内部コンパイラスタックの先頭からレコードを削除します。 *N*が**pop**と共に指定されていない場合、スタックの一番上にある結果のレコードに関連付けられているパッキング値が新しいパッキングアラインメント値になります。 *N*が指定されている場合`#pragma pack(pop, 16)`、たとえば、n が新しいパッキングアラインメント値になります。 などの`#pragma pack(pop, r1)`*識別子*を使用して pop を使用すると、*識別子*を持つレコードが見つかるまでスタック上のすべてのレコードがポップされます。 そのレコードがポップされ、スタックの一番上にある結果のレコードに関連付けられているパッキング値が新しいパッキングアラインメント値になります。 スタック上のどのレコードにも存在しない*識別子*を使用して pop を使用すると、 **pop**は無視されます。

*識別子*\
Optional**Push**と共に使用すると、内部コンパイラスタックのレコードに名前が割り当てられます。 **Pop**と共に使用すると、*識別子*が削除されるまでレコードを内部スタックからポップします。 *識別子*が内部スタックで見つからない場合は、何もポップされません。

*n*\
Optionalパッキングに使用する値をバイト単位で指定します。 コンパイラオプション[/zp](../build/reference/zp-struct-member-alignment.md)がモジュールに対して設定されていない場合、 *n*の既定値は8になります。 有効値は 1、2、4、8、および 16 です。 メンバーの配置は、 *n*の倍数またはメンバーのサイズの倍数のいずれか小さい方の境界上にあります。

`#pragma pack(pop, identifier, n)`定義されていません。

## <a name="remarks"></a>Remarks

クラスを*パック*するには、そのメンバーをメモリ内で相互に直接配置します。 一部またはすべてのメンバーを、ターゲットアーキテクチャの既定の配置よりも小さい境界に配置できることを意味します。 **パック**は、データ宣言レベルでコントロールを提供します。 これは、モジュールレベルのコントロールのみを提供するコンパイラオプション[/zp](../build/reference/zp-struct-member-alignment.md)とは異なります。 **パッケージ**は、プラグマが表示された後、最初の**構造体**、**共用体**、または**クラス**の宣言で有効になります。 **パック**は定義に影響しません。 引数を指定せずにを呼び出すと、 *n*はコンパイラオプション`/Zp`で設定された値に設定されます。 コンパイラオプションが設定されていない場合、既定値は8です。

構造体の配置を変更すると、メモリの領域はそれほど使用されていなくても、パフォーマンスが低下したり、アラインメントされていないアクセスについてハードウェアで生成された例外を受け取る場合があります。  [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)を使用して、この例外の動作を変更できます。

配置を変更する方法の詳細については、次の記事を参照してください。

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [構造体のアラインメントの例](../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 固有)

   > [!WARNING]
   > Visual Studio 2015 以降では、標準の整列**nas**と**alignof**演算子を使用できます。 `__alignof`これ`declspec( align )`は、とは異なり、コンパイラ間で移植できます。 標準C++ではパッキングが解決されないので、**パック**(または他のコンパイラでは対応する拡張機能) を使用して、ターゲットアーキテクチャのワードサイズより小さいアラインメントを指定する必要があります。

## <a name="examples"></a>使用例

次のサンプルは、 **pack**プラグマを使用して構造体のアラインメントを変更する方法を示しています。

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

次の例では、*プッシュ*、*ポップ*、および*表示*の各構文を使用する方法を示します。

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)