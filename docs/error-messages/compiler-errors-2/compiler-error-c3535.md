---
title: コンパイラ エラー C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: e80fa62db9795838980c63e113300a554afabef3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040862"
---
# <a name="compiler-error-c3535"></a>コンパイラ エラー C3535

'type1' から 'type2' の型を推測できません。

宣言された変数の型、`auto`キーワードは、初期化式の型から推測できません。 初期化式を評価する場合、このエラーが発生します`void`、これは型ではありません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 初期化式の型がないことを確認`void`します。

1. 宣言が基本型へのポインターでないことを確認します。 詳細については、次を参照してください。[基本的な型](../../cpp/fundamental-types-cpp.md)します。

1. 宣言型へのポインターの場合、初期化式がポインター型であることを確認します。

## <a name="example"></a>例

初期化式が評価されるため、次の例で C3535`void`します。

```
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>例

ステートメントの変数を宣言するため、次の例で C3535`x`推測される型をただし初期化子の型へのポインターとして式をダブルクリックします。 その結果、コンパイラは変数の型を推測できません。

```
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>例

次の例では C3535 のため変数`p`推測される型へのポインターを宣言しますが、初期化式がポインター型ではありません。

```
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>関連項目

[auto キーワード](../../cpp/auto-keyword.md)<br/>
[基本的な型](../../cpp/fundamental-types-cpp.md)