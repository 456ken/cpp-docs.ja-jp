---
title: __ud2
ms.date: 11/04/2016
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: a36ab5c25ac9138b2a4d6810cc2a339e534f1695
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029409"
---
# <a name="ud2"></a>__ud2

**Microsoft 固有の仕様**

未定義の命令を生成します。

## <a name="syntax"></a>構文

```
void __ud2();
```

## <a name="remarks"></a>Remarks

プロセッサでは、未定義の命令を実行する場合に無効な opcode 例外が発生します。

`__ud2`関数は、`UD2`マシン語命令、およびカーネル モードでのみ使用できます。 詳細については、ドキュメントの検索"Intel アーキテクチャ ソフトウェア デベロッパーズ マニュアル、ボリューム 2。命令の参照を設定、"で、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)サイト。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__ud2`|x86、x64|

**ヘッダー ファイル** \<intrin.h >

**Microsoft 固有の仕様はここまで**

## <a name="example"></a>例

次の例では、例外を発生させます。 未定義の命令を実行します。 例外ハンドラーは、0 から 1 つに次のリターン コードを変更します。

```
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)