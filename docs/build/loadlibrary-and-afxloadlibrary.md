---
title: LoadLibrary と AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: 96b8c0ce1116dbb08260573f25f941ca54169127
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273790"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary と AfxLoadLibrary

呼び出し処理[LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)または[LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(または[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) に DLL を明示的にリンクします。 この関数が正常終了した場合、呼び出し元プロセスのアドレス空間に指定された DLL が割り当てられ、DLL へのハンドルが返されます。このハンドルは、`GetProcAddress` や `FreeLibrary` など、明示的リンクに必要な他の関数で使用できます。

`LoadLibrary` は、暗黙リンクと同じ検索シーケンスで DLL を探します。 システムが DLL を見つけられない場合、またはエントリ ポイント関数が FALSE を返した場合、`LoadLibrary` は NULL を返します。 `LoadLibrary` への呼び出しで指定される DLL モジュールが呼び出し元プロセスのアドレス空間に既に割り当てられている場合、この関数は DLL のハンドルを返し、モジュールの参照カウントをインクリメントします。

DLL にエントリ ポイント関数が含まれる場合、オペレーティング システムは、`LoadLibrary` を呼び出したスレッドのコンテキスト内でその関数を呼び出します。 `LoadLibrary` の前回の呼び出しに対応する `FreeLibrary` 関数呼び出しが行われていないために、DLL が既にプロセスにアタッチされている場合は、エントリ ポイント関数は呼び出されません。

MFC 拡張 Dll を読み込む MFC アプリケーションでは、私たちにを使用することお勧め`AfxLoadLibrary`の代わりに`LoadLibrary`します。 `AfxLoadLibrary` を呼び出す前に、`LoadLibrary` でスレッド同期を処理します。 `AfxLoadLibrary` のインターフェイス (関数プロトタイプ) は、`LoadLibrary` と同じです。

Windows が DLL を読み込むことができない場合は、プロセスでエラーからの回復を試みることができます。 たとえば、プロセスがユーザーにエラーを通知して、ユーザーに DLL への別のパスを指定するよう要求できます。

> [!IMPORTANT]
> すべての Dll の完全なパスを指定してください。 ファイルが読み込まれるときに、現在のディレクトリを最初に検索します。 ファイルのパスを指定していないと、目的のファイルでないファイルが読み込まれる場合があります。 これを防ぐために別の方法を使用して、 [/DEPENDENTLOADFLAG](reference/dependentloadflag.md)リンカー オプション。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#linking-implicitly)

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [ダイナミック リンク ライブラリの検索順序](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary と AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>関連項目

- [Visual C++ の DLL](dlls-in-visual-cpp.md)
