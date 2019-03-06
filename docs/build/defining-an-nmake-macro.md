---
title: NMAKE マクロの定義
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 6eb7c2f7759bda21f1424cef91b1dc814ba8d8ba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424107"
---
# <a name="defining-an-nmake-macro"></a>NMAKE マクロの定義

## <a name="syntax"></a>構文

```

macroname=string
```

## <a name="remarks"></a>Remarks

*Macroname*は英字、数字、および最大 1,024 文字、アンダー スコア (_) の組み合わせでありはケースを区別します。 *Macroname*呼び出されたマクロを含めることができます。 場合*macroname*は、呼び出されたマクロの完全、呼び出されているマクロを null または未定義することはできません。

`string` 0 個以上の文字のシーケンスを指定できます。 Null 文字列には、0 文字または空白またはタブだけが含まれています。 `string`マクロ呼び出しを含めることができます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[マクロの特殊文字](../build/special-characters-in-macros.md)

[Null と未定義マクロ](../build/null-and-undefined-macros.md)

[マクロを定義する場所](../build/where-to-define-macros.md)

[マクロ定義の優先順位](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>関連項目

[マクロと NMAKE](../build/macros-and-nmake.md)
