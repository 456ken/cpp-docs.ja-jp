---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 20efdc755b7f706fc6ee962daa32bd352df39d45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159770"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

外部ファイルに格納されているシーケンスの iostream の操作をサポートする複数のクラスを定義します。

## <a name="syntax"></a>構文

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|型`basic_filebuf`に特殊化された**char**テンプレート パラメーター。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|型`basic_fstream`に特殊化された**char**テンプレート パラメーター。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|型`basic_ifstream`に特殊化された**char**テンプレート パラメーター。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|型`basic_ofstream`に特殊化された**char**テンプレート パラメーター。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|型`basic_fstream`に特殊化された**wchar_t**テンプレート パラメーター。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|型`basic_ifstream`に特殊化された**wchar_t**テンプレート パラメーター。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|型`basic_ofstream`に特殊化された**wchar_t**テンプレート パラメーター。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|型`basic_filebuf`に特殊化された**wchar_t**テンプレート パラメーター。|

### <a name="classes"></a>クラス

|クラス|説明|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|このテンプレート クラスは、文字の特徴がクラス `Tr` によって決まる型 `Elem` の要素と、外部ファイルに格納されている要素のシーケンスとの間でやり取りされる転送を制御するストリーム バッファーを記述します。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|テンプレート クラスは、要素の挿入と抽出を制御するオブジェクトとクラスのストリーム バッファーを使用してエンコードされたオブジェクトについて説明します[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**、  **。Tr**>、型の要素を含む`Elem`、その文字特性はクラスによって決まります`Tr`します。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|テンプレート クラスは、クラスのストリーム バッファーからエンコードされたオブジェクトと要素の抽出を制御するオブジェクトについて説明します[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**、 **Tr**。>、型の要素を含む`Elem`、その文字特性はクラスによって決まります`Tr`します。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|テンプレート クラスは、クラスのストリーム バッファーにエンコードされたオブジェクトと要素の挿入を制御するオブジェクトを説明します[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**、 **Tr**。>、型の要素を含む`Elem`、その文字特性はクラスによって決まります`Tr`します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream プログラミング](../standard-library/iostream-programming.md)<br/>
[iostreams の規則](../standard-library/iostreams-conventions.md)<br/>
