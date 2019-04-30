---
title: ガイド付き最適化のプロファイルのエラー PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359736"
---
# <a name="profile-guided-optimization-error-pg0165"></a>ガイド付き最適化のプロファイルのエラー PG0165

'Filename.pgd' を読み込み中には。' PGD バージョンがサポートされていません (バージョンの不一致)' です。

PGD ファイルは、特定のコンパイラ ツールセットに固有です。 別のコンパイラを使用したものを使用しているときにこのエラーは生成*Filename*.pgd します。 このエラーは、このコンパイラ ツールセットからデータを使用できないことを示します*Filename*.pgd を現在のプログラムを最適化します。

この問題を解決するには、再生成*Filename*.pgd、現在のコンパイラ ツールセットを使用しています。