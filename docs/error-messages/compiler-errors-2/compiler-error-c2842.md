---
title: コンパイラ エラー C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 99b2c86d1e914c9425c2664d4e858bba6cb99486
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325569"
---
# <a name="compiler-error-c2842"></a>コンパイラ エラー C2842

> '*クラス*': マネージまたは WinRT 型では、独自 'operator new' が定義されていない可能性がありますか、'operator delete'

## <a name="remarks"></a>Remarks

独自に定義することができます**演算子 new**または**delete 演算子**ネイティブ ヒープにメモリの割り当てを管理します。 ただし、これらの演算子はマネージド ヒープでのみ割り当てられるため、参照クラスでは定義できません。

詳細については、[ユーザー定義演算子 (C +/cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)を参照してください。

## <a name="example"></a>例

次の例では C2842 が生成されます。

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
