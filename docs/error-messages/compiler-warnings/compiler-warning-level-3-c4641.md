---
title: コンパイラの警告 (レベル 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 9357088106a45026eae543f8627ea59988e73995
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401671"
---
# <a name="compiler-warning-level-3-c4641"></a>コンパイラの警告 (レベル 3) C4641

XML ドキュメント コメントは、あいまいな相互参照

コンパイラは、明確に参照を解決できませんでした。 この警告を解決するには、参照を明確に必要なパラメーター情報を指定します。

詳細については、「 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4641 が生成されます。

```
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```