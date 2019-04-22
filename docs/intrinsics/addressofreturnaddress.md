---
title: _AddressOfReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 79d1e4645c60fb4231a53aaefdcf1fe0f3c876c4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024778"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 固有の仕様**

現在の関数の戻り値のアドレスを保持するメモリの場所のアドレスを提供します。 このアドレスを使用して、その他のメモリ位置 (たとえば、関数の引数) にアクセスすることはできません。

## <a name="syntax"></a>構文

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86、x64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

ときに`_AddressOfReturnAddress`でコンパイルされたプログラムで使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)、関数を含む、`_AddressOfReturnAddress`呼び出しは、ネイティブ関数としてコンパイルされます。 含まれる関数呼び出しとして関数をコンパイルするときに管理されている`_AddressOfReturnAddress`、`_AddressOfReturnAddress`期待どおりに動作しない可能性があります。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)<br/>
[キーワード](../cpp/keywords-cpp.md)