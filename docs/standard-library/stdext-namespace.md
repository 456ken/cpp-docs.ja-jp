---
title: stdext 名前空間
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: d40f3f7a99db72784cc9a32a9c37064228597d34
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750534"
---
# <a name="stdext-namespace"></a>stdext 名前空間

メンバー、 [ \<hash_map >](../standard-library/hash-map.md)と[ \<hash_set >](../standard-library/hash-set.md)現在 ISO C 標準の一部がヘッダー ファイルではないです。 そのため、これらの型およびメンバーは、C++ の標準に準拠するように、名前空間 `std` から名前空間 `stdext`に移動されました。

コンパイルするときに[/Ze](../build/reference/za-ze-disable-language-extensions.md)、コンパイラの警告の使用に、既定では、これは`std`のメンバーに対して、 \<hash_map > と\<hash_set > ヘッダー ファイル。 この警告を無効にするには、 [warning](../preprocessor/warning.md) プラグマを使用します。

コンパイラでの使用に対してエラーを生成する`std`のメンバーの\<hash_map > と\<hash_set > ヘッダー ファイルを **/Ze**、追加する前に、次のディレクティブ`#include`C++ 標準ライブラリ ヘッダー ファイル。

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

コンパイルするときに **/Za**、コンパイラ エラーが発生します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)
