---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: c29ec47170c5e0f46f02d53f23ab477a79bbdc32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205226"
---
# <a name="savexmm128"></a>.SAVEXMM128

いずれかが生成されます、`UWOP_SAVE_XMM128`または`UWOP_SAVE_XMM128_FAR`アンワインド コードのエントリの指定の XMM レジスタと現在のプロローグのオフセットを使用してオフセットします。 MASM は、最も効率的なエンコーディングを選択します。

## <a name="syntax"></a>構文

> .savexmm128 xmmreg、オフセット

## <a name="remarks"></a>Remarks

.フレームの関数のアンワインドされるとから拡張すると、プロローグ内でのみ許可が指定できる ml64.exe の SAVEXMM128、 [PROC](../../assembler/masm/proc.md)フレームの宣言、[します。ENDPROLOG](../../assembler/masm/dot-endprolog.md)ディレクティブ。 これらのディレクティブは、コードを生成しませんのみを生成する`.xdata`と`.pdata`します。 .SAVEXMM128 は、実際にアンワインド操作を実装する手順によって先行されなければなりません。 アンワインド ディレクティブと契約を確認します。 マクロでのアンワインドに本来はコードの両方をラップすることをお勧めします。

*オフセット*16 の倍数である必要があります。

詳細については、次を参照してください。 [x64 用 MASM (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)します。

## <a name="see-also"></a>関連項目

[ディレクティブ リファレンス](../../assembler/masm/directives-reference.md)<br/>