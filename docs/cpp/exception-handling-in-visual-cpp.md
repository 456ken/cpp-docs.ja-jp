---
title: MSVC の例外処理
ms.date: 05/07/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 47443f1b7021aac7755d77f797a4f7b7410281f8
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222071"
---
# <a name="exception-handling-in-msvc"></a>MSVC の例外処理

例外とは、プログラムが通常の実行パスに沿って進むことを妨げるエラー状態のことであり、プログラムで制御できない可能性があります。 オブジェクトの作成、ファイルの入出力、および他のモジュールから行われる関数呼び出しを含む特定のアクションは、プログラムが正しく実行されている場合でも、すべて例外の潜在的な原因となります。 堅牢なコードは例外を予期し、それを処理します。

1 つのプログラムまたはモジュール内のロジック エラーを検出するために、例外ではなくアサーションを使用して (を参照してください[を使用してアサーション](/visualstudio/debugger/c-cpp-assertions))。

MicrosoftC++コンパイラ (MSVC) は、次の 3 つの種類の例外処理をサポートしています。

- [C++ 例外処理](../cpp/cpp-exception-handling.md)

   ほとんどの C++ プログラムでは、タイプ セーフでオブジェクトのデストラクターがスタック アンワインド中に確実に呼び出されるようにする、C++ 例外処理を使用する必要があります。

- [構造化例外処理](../cpp/structured-exception-handling-c-cpp.md)

   Windows には、SEH と呼ばれる独自の例外機構が備わっています。 これは C++ または MFC プログラミングには推奨されません。 非 MFC C プログラムでのみ、SEH を使用します。

- [MFC 例外](../mfc/exception-handling-in-mfc.md)

   MFC はバージョン 3.0 以降、C++ 例外を使用していますが、フォームの C++ 例外に似た古い例外処理マクロを引き続きサポートします。 これらのマクロは新しいプログラミングで推奨されませんが、下位互換性のために引き続きサポートされます。 既にマクロを使用しているプログラムでは、自由に C++ の例外も使用できます。 前処理中には、例外処理の MSVC の実装で定義されているキーワードに評価されるマクロ、C++時点で、ビジュアル言語C++バージョン 2.0。 C++ 例外処理の使用を開始するときは、既存の例外処理マクロをそのまま維持できます。

使用して、 [/EH](../build/reference/eh-exception-handling-model.md) ; プロジェクトで使用する例外処理の種類を指定するコンパイラ オプションC++ 例外処理では、既定値です。 エラー処理機構を併用しないでください。たとえば、構造化例外処理で C++ 例外を使用しないでください。 C++ 例外処理を使用すると、コードの移植性が高くなり、すべての種類の例外を処理できるようになります。 構造化例外処理の欠点の詳細については、次を参照してください。[構造化例外処理](../cpp/structured-exception-handling-c-cpp.md)します。 MFC マクロと C++ の例外についてのアドバイスを参照してください。[例外。MFC マクロと C++ 例外を使用して](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)します。

CLR アプリケーションで例外を処理する方法の詳細については、次を参照してください。[例外処理 (C +/cli および C++/cli CX)](../extensions/exception-handling-cpp-component-extensions.md)します。

X64 の例外処理については、プロセッサを参照してください[x64 例外処理](../build/exception-handling-x64.md)します。

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)