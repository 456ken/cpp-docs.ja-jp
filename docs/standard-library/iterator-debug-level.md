---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: a584fe5a97e251205e750507b27e53e6e7b9a20e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224195"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL マクロ コントロールかどうか[反復子がチェック](../standard-library/checked-iterators.md)と[デバッグ反復子のサポート](../standard-library/debug-iterator-support.md)を有効にします。 このマクロよりも優先され、以前の _SECURE_SCL および _HAS_ITERATOR_DEBUGGING マクロの機能を結合します。

## <a name="macro-values"></a>マクロの値

次の表では、_ITERATOR_DEBUG_LEVEL マクロの値をまとめたものです。

|コンパイル モード|マクロの値|説明|
|----------------------|----------------|-----------------|
|**Debug**|||
||0|チェックを行う反復子を無効にし、反復子のデバッグを無効にします。|
||1|チェックを行う反復子を有効にし、反復子のデバッグを無効にします。|
||2 (既定値)|反復子のデバッグを有効にします。チェックを行う反復子は関連しません。|
|**Release**|||
||0 (既定値)|チェックを行う反復子を無効にします。|
||1|チェックを行う反復子を有効にします。反復子のデバッグは関連しません。|

リリース モードでは、コンパイラは、_ITERATOR_DEBUG_LEVEL を 2 として指定する場合に、エラーを生成します。

## <a name="remarks"></a>Remarks

_ITERATOR_DEBUG_LEVEL マクロ コントロールかどうか[反復子がチェック](../standard-library/checked-iterators.md)が有効にして、デバッグ モードでかどうか、[デバッグ反復子のサポート](../standard-library/debug-iterator-support.md)を有効にします。 _ITERATOR_DEBUG_LEVEL が 1 または 2 として定義される場合、checked 反復子は、コンテナーの境界が上書きされないことを確認します。 _ITERATOR_DEBUG_LEVEL が 0 の場合、反復子はチェックされません。 _ITERATOR_DEBUG_LEVEL が 1 として定義されると、反復子の安全でない使用によってランタイム エラーが発生し、プログラムが終了します。 _ITERATOR_DEBUG_LEVEL は 2 として定義されている、安全でない反復子は、アサートとすることができます、ランタイム エラー ダイアログがデバッガーに割り込む原因を使用します。

_ITERATOR_DEBUG_LEVEL マクロが、_SECURE_SCL マクロおよび _HAS_ITERATOR_DEBUGGING マクロと同様の機能をサポートするため、場合があります特定するマクロおよびマクロは、特定の状況で使用する値します。 混乱を防ぐためには、_ITERATOR_DEBUG_LEVEL マクロのみを使用することをお勧めします。 このテーブルには、_SECURE_SCL と既存のコードで _HAS_ITERATOR_DEBUGGING のさまざまな値を使用する同等の _ITERATOR_DEBUG_LEVEL マクロの値について説明します。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (リリースの既定値)|0 (無効)|0 (無効)|
|1|1 (有効)|0 (無効)|
|2 (デバッグの既定値)|(関連性なし)|1 (デバッグ モードで有効)|

チェックを行う反復子に関する警告を無効にする方法の詳細については、「[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)」を参照してください。

### <a name="example"></a>例

_ITERATOR_DEBUG_LEVEL マクロの値を指定するには、使用、 [/D](../build/reference/d-preprocessor-definitions.md)コンパイラ オプションで、コマンドラインで定義または使用`#define`する前に、C++標準ライブラリ ヘッダーは、ソース ファイルに含まれます。 コンパイル、コマンドラインでなど*sample.cpp*デバッグ モードで、反復子のデバッグのサポートを使用するには、_ITERATOR_DEBUG_LEVEL マクロの定義を指定することができます。

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

ソース ファイルで、反復子を定義する標準ライブラリ ヘッダーの前にマクロを指定します。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>関連項目

[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
