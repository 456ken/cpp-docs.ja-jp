---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348309"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

C++ 標準ライブラリで安全でないメソッドのいずれかの呼び出しの結果[コンパイラの警告 (レベル 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)します。 この警告を無効にするには、コードでマクロ _SCL_SECURE_NO_WARNINGS を定義します。

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

プリコンパイル済みヘッダーを使用する場合は、任意の C ランタイム ライブラリまたは標準ライブラリ ヘッダーをインクルードする前に、このディレクティブをプリコンパイル済みヘッダー ファイル内に配置します。 配置した場合に、個々 のソース コード ファイルでプリコンパイル済みヘッダー ファイルをインクルードする前に、コンパイラによって無視されます。

## <a name="remarks"></a>Remarks

警告 C4996 を無効にするその他の方法は、次のとおりです。

- [/D (プリプロセッサの定義)](../build/reference/d-preprocessor-definitions.md) コンパイラ オプションの使用:

   > cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp

- [/w](../build/reference/compiler-option-warning-level.md) コンパイラ オプションの使用:

   > cl /wd4996 [other compiler options] myfile.cpp

- [#pragma 警告](../preprocessor/warning.md) ディレクティブの使用:

   ```cpp
   #pragma warning(disable:4996)
   ```

また、**/w\<l>\<n>** コンパイラ オプションを使用して、警告 C4996 のレベルを手動で変更できます。 たとえば、警告 C4996 をレベル 4 に設定します。

> cl /w44996 [other compiler options] myfile.cpp

詳細については、「[/w、/W0、/W1、/W2、/W3、/W4, /w1, /w2, /w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告レベル)](../build/reference/compiler-option-warning-level.md)」を参照してください。

## <a name="see-also"></a>関連項目

[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
