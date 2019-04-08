---
title: コンパイラ エラー C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 117c9b9918950fd2e95e206c5aea457dee183b0a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781576"
---
# <a name="compiler-error-c3465"></a>コンパイラ エラー C3465

型 'type' を使用するには、アセンブリ 'assembly' を参照しなければなりません

クライアント アプリケーションで型の転送が機能するのは、クライアントを再コンパイルするまでの間です。 再コンパイルする場合は、クライアント アプリケーションで使用される型の定義を含む各アセンブリの参照が必要です。

詳細については、次を参照してください。 [Type Forwarding (C +/cli CLI)](../../extensions/type-forwarding-cpp-cli.md)します。

## <a name="example"></a>例

次の例では、型の新しい場所を含むアセンブリを作成します。

```
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>例

次の例は型定義を含んでいたアセンブリを作成しますが、今回は型の転送構文が含まれています。

```
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>例

次の例では C3465 が生成されます。

```
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```