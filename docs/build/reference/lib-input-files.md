---
title: LIB の入力ファイル
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: fb0095bd9e8699fbc9a1a144833d12d2cf4a1f83
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423093"
---
# <a name="lib-input-files"></a>LIB の入力ファイル

LIB で想定されている入力ファイルは、次の表に示すように、モードによって異なります。

|モード|入力|
|----------|-----------|
|既定値 (構築またはライブラリの変更)|COFF オブジェクト (.obj) ファイル、32 ビット omf オブジェクト モデルの形式 (です) のオブジェクト (.obj) ファイルである COFF ライブラリ (.lib)|
|/EXTRACT でメンバーの抽出|COFF ライブラリ (.lib)|
|ファイルし、/DEF ライブラリをインポート、エクスポートの構築|モジュール定義 (.def) ファイル、COFF オブジェクト (.obj) ファイル、COFF ライブラリ (.lib)、32 ビット OMF オブジェクト (.obj) ファイル|

> [!NOTE]
>  16 ビット版の LIB によって作成された OMF ライブラリは、LIB の 32 ビット バージョンへの入力として使用できません。

## <a name="see-also"></a>関連項目

[LIB の概要](../../build/reference/overview-of-lib.md)
