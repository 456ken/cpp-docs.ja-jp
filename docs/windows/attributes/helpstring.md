---
title: helpstring (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 623b2c7fb4ce7c3e5de87d21f012d008720fdee2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409591"
---
# <a name="helpstring"></a>helpstring

適用先となる要素を記述するために使用される文字列を指定します。

## <a name="syntax"></a>構文

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>パラメーター

*string*<br/>
ヘルプ文字列のテキスト。

## <a name="remarks"></a>Remarks

**Helpstring** C++ 属性と同じ機能を持つ、 [helpstring](/windows/desktop/Midl/helpstring) MIDL 属性。

## <a name="example"></a>例

例をご覧ください[defaultvalue](defaultvalue.md)を使用する方法の例については**helpstring**します。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**インターフェイス**、 **typedef**、**クラス**メソッド、プロパティ|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)