---
title: プリプロセッサ演算子
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 1c556e4af5913ba8d0dc7efc9648e0d0004d9d7e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222250"
---
# <a name="preprocessor-operators"></a>プリプロセッサ演算子

`#define`ディレクティブのコンテキストでは、4つのプリプロセッサ固有の演算子が使用されます。 各の概要については、次の表を参照してください。 文字列化、文字定数化、およびトークン連結演算子については、次の 3 つのセクションで説明します。 `defined`演算子の詳細については、「 [#if、#elif、#else、および #endif ディレクティブ](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)」を参照してください。

|演算子|アクション|
|--------------|------------|
|[文字列化演算子 (#)](../preprocessor/stringizing-operator-hash.md)|対応する実引数が二重引用符で囲まれます|
|[文字化演算子 (# @)](../preprocessor/charizing-operator-hash-at.md)|対応する引数が単一引用符で囲まれ、文字として処理されます (Microsoft 固有の仕様)|
|[トークン連結演算子 (# #)](../preprocessor/token-pasting-operator-hash-hash.md)|実引数として使用されるトークンが、他のトークンを形成するために連結されることを許可します|
|[定義された演算子](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|特定のマクロ ディレクティブで複合式の記述を簡略化します|

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)\
[定義済みマクロ](../preprocessor/predefined-macros.md)\
[c/c + + プリプロセッサリファレンス](../preprocessor/c-cpp-preprocessor-reference.md)
