---
title: C 言語 API との関係
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: fe83af2d05af8e3b9da8d0c62f6974b0a5410bfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308984"
---
# <a name="relationship-to-the-c-language-api"></a>C 言語 API との関係

Windows の他のクラス ライブラリとは別に、Microsoft Foundation Class (MFC) ライブラリを設定する特性の 1 つは、C 言語で記述された Windows API に非常に閉じるマッピングです。 さらを混在させることがクラス ライブラリの呼び出しを自由に Windows API を直接呼び出すとします。 この直接アクセスは、ただし、限りませんクラスは、その api に完全に置き換えること。 開発者がなど一部の Windows 関数への直接呼び出しを行う場合によってはまだ必要があります[以前](/windows/desktop/api/winuser/nf-winuser-setcursor)と[GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics)など。 そう明確な利点がある場合にのみ Windows 関数がクラス メンバー関数でラップされます。

ネイティブ Windows 関数の呼び出しを行う必要がある場合があります、ために、C 言語の Windows API のドキュメントへのアクセスが必要です。 このドキュメントは、Microsoft Visual C に含まれています。

> [!NOTE]
>  MFC ライブラリのフレームワークの動作方法の概要については、次を参照してください。 [Windows のアプリケーションを記述するクラスを使用して](../mfc/using-the-classes-to-write-applications-for-windows.md)します。

## <a name="see-also"></a>関連項目

[一般的なクラス デザインの考え方](../mfc/general-class-design-philosophy.md)
