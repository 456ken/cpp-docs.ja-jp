---
title: コンパイラの警告 (レベル 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: c194e19c8766b67eb7deef32e7228564cda5f1e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406380"
---
# <a name="compiler-warning-level-1-c4691"></a>コンパイラの警告 (レベル 1) C4691

'type': 参照されていないアセンブリ 'file' を代わりに使用される現在の翻訳単位で定義された型で参照される型が必要です

元の型定義を含むメタデータ ファイルが参照されていないと、コンパイラは、ローカルの型定義を使用しています。

場合は、再構築する、*ファイル*、C4691 を無視またはプラグマでになっていることができます[警告](../../preprocessor/warning.md)します。  つまり、構築しているファイル、コンパイラは型定義を検索するファイルと同じである場合は、C4691 を無視できます。

ただし、予期しない動作ことができます、コンパイラは、同じアセンブリのメタデータで参照されているからではない定義を使用している場合に発生します。CLR 型は、型の名前だけでなく、アセンブリによっても型指定されます。  これはアセンブリ z.dll から Z の型はアセンブリ y.dll から型 Z と異なるがあります。

## <a name="example"></a>例

このサンプルには、元の型定義が含まれています。

```
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>例

このサンプルでは、C4691_a.dll を参照し、Original_Type 型のフィールドを宣言します。

```
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>例

次の例では、C4691 が生成されます。  このサンプル Original_Type の定義が含まれていて C4691a.dll を参照していません確認します。

を解決するには、元の型定義を含むメタデータ ファイルを参照し、ローカル宣言と定義を削除します。

```
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```