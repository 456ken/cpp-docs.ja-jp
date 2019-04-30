---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: eb73c77f0e2658cf750cf17ca85549a09d1cbe51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370932"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

テンプレート クラス [basic_ostream](../standard-library/basic-ostream-class.md) を定義します。これは iostreams への挿入を仲介します。 ヘッダーは、関連する複数のマニピュレーターを定義します  (通常このヘッダーは、別の iostream ヘッダーに含まれています。 まれに、直接含めなければならないことがあります)。

## <a name="syntax"></a>構文

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|型を作成します。`basic_ostream`に特殊化した**char**と`char_traits`に特殊化された**char**します。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|型を作成します。`basic_ostream`に特殊化した**wchar_t**と`char_traits`に特殊化された**wchar_t**します。|

### <a name="manipulators"></a>マニピュレーター

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|行を終了し、バッファーをフラッシュします。|
|[ends](../standard-library/ostream-functions.md#ends)|文字列を終了します。|
|[flush](../standard-library/ostream-functions.md#flush)|バッファーをフラッシュします。|
|[swap](../standard-library/ostream-functions.md#swap)|左側の `basic_ostream` オブジェクト パラメーターの値と右側の `basic_ostream` オブジェクト パラメーターの値を交換します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|さまざまな型をストリームに書き込みます。|

### <a name="classes"></a>クラス

|クラス|説明|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|このテンプレート クラスは、要素とエンコードされたオブジェクトをストリーム バッファーに挿入する操作を制御するオブジェクトを記述します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream プログラミング](../standard-library/iostream-programming.md)<br/>
[iostreams の規則](../standard-library/iostreams-conventions.md)<br/>
