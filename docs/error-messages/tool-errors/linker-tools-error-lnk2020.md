---
title: リンカ ツール エラー LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 7290a90dfd92d84c4632e7f9dd38d36eccd4ac27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386331"
---
# <a name="linker-tools-error-lnk2020"></a>リンカ ツール エラー LNK2020

未解決のトークン 'token'

未定義の外部エラーに似ていますが、参照はメタデータを使用して、します。 メタデータで、すべての関数とデータを定義する必要があります。

解決します。

- 不足している関数またはデータ定義または

- オブジェクト ファイルまたは不足している関数またはデータが既に定義されているライブラリが含まれます。

## <a name="example"></a>例

次の例では、LNK2020 が生成されます。

```
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>例

LNK2020 が、管理対象のテンプレートの種類の変数を作成することが、型をインスタンス化しない場合にも発生します。

次の例では、LNK2020 が生成されます。

```
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```