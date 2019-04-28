---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 342c8acd95fd45de1a21dc298325de9a7b40b717
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179108"
---
# <a name="comm"></a>COMM

指定された属性を持つ土台の変数を作成します。*定義*します。

## <a name="syntax"></a>構文

> **COMM** *definition* [, *definition*] ...

## <a name="remarks"></a>Remarks

土台の変数は、リンカーによって割り当てられているし、初期化することはできません。 これは、場所やこのような変数の順序に依存できないことを意味します。

各*定義*は次の形式があります。

[*langtype*] [**NEAR** &#124; **FAR**] _label_**:**_type_[**:**_count_]

省略可能な*langtype*に続く名前の名前付け規則を設定します。 指定された任意の言語よりも優先、**します。モデル**ディレクティブ。 省略可能な**NEAR**または**FAR**現在のメモリ モデルをオーバーライドします。 *ラベル*変数の名前を指定します。 *型*任意の型指定子を指定できます ([バイト](../../assembler/masm/byte-masm.md)、 [WORD](../../assembler/masm/word.md)など) またはバイト数を指定する整数。 省略可能な*カウント*宣言されたデータ オブジェクトの要素の数を指定します。 既定値は 1 つです。

## <a name="example"></a>例

この例では、512 バイトの要素の配列を作成します。

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>関連項目

[ディレクティブ リファレンス](../../assembler/masm/directives-reference.md)<br/>
