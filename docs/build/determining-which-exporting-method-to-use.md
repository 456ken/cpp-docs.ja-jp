---
title: エクスポート方式の使い分け
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 38006acfae90c3b216677684e9776f3ed5d7c1b1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422759"
---
# <a name="determining-which-exporting-method-to-use"></a>エクスポート方式の使い分け

2 つの方法のいずれかで関数をエクスポートする — .def ファイルまたは`__declspec(dllexport)`キーワード。 DLL のより優れた方法を決定するために、これらの質問を考慮してください。

- 後でより多くの関数をエクスポートする予定ですか。

- DLL を再構築することができます、または再構築することはできませんのアプリケーションで使用するアプリケーションでのみ使用されるは、サード パーティによって作成されるアプリケーションなどでしょうか。

## <a name="pros-and-cons-of-using-def-files"></a>.Def ファイルを使用しての長所と短所

エクスポート序数を制御できる .def ファイルのための関数をエクスポートします。 DLL にエクスポートされた関数を追加する場合は、他のエクスポートされた関数よりも高い序数値を割り当てることができます。 これを行うときに暗黙的なリンクを使用するアプリケーションを新しい関数を含むインポート ライブラリと再リンクする必要はありません。 これは、新しい機能を追加しても既にそれに依存するアプリケーションで正しく動作し続けることを確認できるので、多くのアプリケーションで使用するための DLL をデザインしている場合に非常に便利です。 たとえば、MFC の Dll は、.def ファイルを使用して構築されます。

.Def ファイルを使用して、もう 1 つの利点は、使用できる、`NONAME`関数をエクスポートする属性。 これによって、DLL のエクスポート テーブルに、序数のみです。 使用して、エクスポートされた関数は、多数ある Dll を`NONAME`属性は、DLL ファイルのサイズを減らすことができます。 モジュール定義ステートメントを記述する方法については、次を参照してください。[モジュール定義ステートメントに関する規則](../build/reference/rules-for-module-definition-statements.md)します。 序数エクスポートの詳細については、次を参照してください。[関数名ではなく序数による DLL のエクスポート](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)します。

.Def ファイルを使用する場合の欠点は、C++ ファイルで関数をエクスポートする場合いるか、.def に装飾名を格納するファイルまたは extern"C"を使用して、名前の装飾に実行を回避するために、エクスポートされた関数を定義して、Visual C コンパイラ。

使用して取得できます、装飾名を .def ファイルに配置した場合、 [DUMPBIN](../build/reference/dumpbin-reference.md)ツールまたはリンカーを使用して[/map](../build/reference/map-generate-mapfile.md)オプション。 コンパイラによって生成される装飾名はコンパイラ固有です。そのため、.def ファイルに、コンパイラによって生成される装飾名を配置した場合、DLL にリンクしているアプリケーションする必要がありますもビルド呼び出し元のアプリケーション内の装飾名がエクスポートされた一致するように、同じバージョンのコンパイラを使用して、i の名前n DLL の .def ファイル。

## <a name="pros-and-cons-of-using-declspecdllexport"></a>関数を使用しての長所と短所

使用して`__declspec(dllexport)`.def ファイルを管理して、エクスポートされた関数の装飾名の取得について心配する必要はありませんので便利です。 ただし、この方法でエクスポートの有用性は、再構築してもよいリンクされたアプリケーションの数によって制限されます。 新しいエクスポートで DLL を再構築する場合は、再構築するさまざまなバージョンのコンパイラを使用する場合、エクスポートされた C++ 関数の装飾名は変わる可能性があるアプリケーションを再構築する必要があります。

### <a name="what-do-you-want-to-do"></a>実行する操作

- [使用して、DLL からエクスポートします。DEF ファイル](../build/exporting-from-a-dll-using-def-files.md)

- [関数を使った DLL からエクスポートします。](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS を使ったエクスポート/インポート](../build/exporting-and-importing-using-afx-ext-class.md)

- [C 言語の実行可能ファイルで使用するための C++ 関数をエクスポートします。](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C または C++ 言語の実行可能ファイルで使用するための C 関数をエクスポートします。](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [使用してアプリケーションをインポートします。](../build/importing-into-an-application-using-declspec-dllimport.md)

- [DLL を初期化します。](../build/run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [インポートとエクスポートのインライン関数](../build/importing-and-exporting-inline-functions.md)

- [相互インポート](../build/mutual-imports.md)

- [装飾名](../build/reference/decorated-names.md)

## <a name="see-also"></a>関連項目

[DLL からのエクスポート](../build/exporting-from-a-dll.md)
