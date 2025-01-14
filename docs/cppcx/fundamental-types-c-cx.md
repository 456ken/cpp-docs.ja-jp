---
title: 基本的な型 (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 2bd5be01b868fd3086c2064edfd4ca343db425be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301456"
---
# <a name="fundamental-types-ccx"></a>基本的な型 (C++/CX)

だけでなく、標準C++組み込み型C++/CX は、基本的な Windows ランタイムの型にマップする標準の typedef を提供することで、Windows ランタイムのアーキテクチャによって定義される型システムをサポートしているC++型. C++/CX では、ブール値、文字、および数値基本型を実装します。 これらの typedefs は、 `default` 名前空間 (明示的に指定する必要はない) で定義されます。 さらに、 C++/CX ラッパーと具体的な実装を特定の Windows ランタイム型とインターフェイスを提供します。

## <a name="boolean-and-character-types"></a>ブール値および文字の種類

組み込みブール値と文字型、および標準 C++ に相当するものを次の表に一覧表示します。

|名前空間|C++/CX 名前|定義|標準 C++ 名|値の範囲|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|プラットフォーム|ブール型|8 ビットのブール値。|bool|**true** (0 以外) と**false** (ゼロ)|
|default|char16|Unicode (UTF-16) コード ポイントを表す 16 ビットの数字以外の値。|wchar_t<br /><br /> - または -<br /><br /> L'c'|(Unicode 標準によって指定される)|

## <a name="numeric-types"></a>数値型

組み込み数値型を次の表に一覧表示します。 数値型は `default` 名前空間で宣言され、対応する C++ 組み込み型の typedefs です。 Windows ランタイムでは、すべて C++ 組み込む型 (long など) がサポートされています。 一貫性とわかりやすくするため、使用ことが推奨する c++/cli CX の名前。

|C++/CX 名前|定義|標準 C++ 名|値の範囲|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|8 ビット符号付き数値。|signed char|-128 ~ 127|
|uint8|8 ビット符号なし数値。|unsigned char|0 ～ 255|
|int16|16 ビット符号付き整数。|short|-32,768 ~ 32,767|
|uint16|16 ビット符号なし整数。|unsigned short|0 ～ 65,535|
|int32|32 ビット符号付き整数。|int|-2,147, 483,648 ~ 2,147, 483,647|
|uint32|32 ビット符号なし整数。|unsigned int|0 ～ 4,294,967,295|
|int64|64 ビット符号付き整数。|long long  -or- __int64|-9,223,372,036,854、9,223,372,036,854,775,807 を通じて 775,808|
|uint64|64 ビット符号なし整数。|unsigned long long  -or- unsigned __int64|0 ～ 18,446,744,073,709,551,615|
|float32|32 ビットの IEEE 754 浮動小数点数。|float|3.4E +/- 38 (7 桁)|
|float64|64 ビットの IEEE 754 浮動小数点数。|double|1.7E +/- 308 (15 桁)|

## <a name="windows-runtime-types"></a>Windows ランタイム型

次の表に、いくつか追加の型は、Windows ランタイムのアーキテクチャによって定義され、C + に組み込まれているを/cli CX します。 オブジェクトと文字列は参照型です。 それ以外は値型です。 型はすべて、 `Platform` 名前空間で宣言されています。 完全なリストについては、 [Platform namespace](../cppcx/platform-namespace-c-cx.md)を参照してください。

|名|定義|
|----------|----------------|
|Object|任意の Windows ランタイム型を表します。|
|String|テキストを表す一連の文字。|
|Rect|四角形の位置とサイズを表す 4 つ浮動小数点数のセット。|
|SizeT|高さと幅を指定する浮動小数点数の順序付きペア。|
|ポイント|2 次元プレートの位置を定義する浮動小数点の x 座標と y 座標の順序付きペア。|
|Guid|一意の識別子として使用される 128 ビットの数値以外の値。|
|UIntPtr|(内部使用のみ。)ポインターとして使用される符号なし 64 ビット値。|
|IntPtr|(内部使用のみ。)ポインターとして使用される符号付き 64 ビット値。|

## <a name="see-also"></a>関連項目

[型システム](../cppcx/type-system-c-cx.md)
