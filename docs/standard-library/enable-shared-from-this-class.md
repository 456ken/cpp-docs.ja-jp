---
title: enable_shared_from_this クラス
ms.date: 11/04/2016
f1_keywords:
- memory/std::enable_shared_from_this
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
ms.openlocfilehash: 9bf5055aefe505461e81703373ecb042a1f7224a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413724"
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this クラス

`shared_ptr` の生成を支援します。

## <a name="syntax"></a>構文

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>パラメーター

*Ty*<br/>
共有ポインターによって制御される型。

## <a name="remarks"></a>Remarks

`enable_shared_from_this` の派生オブジェクトは、メンバー関数の `shared_from_this` メソッドを使って、既存の `shared_ptr` 所有者と所有権を共有するインスタンスの [shared_ptr](../standard-library/shared-ptr-class.md) 所有者を作成できます。 それ以外の場合、新規に作成する場合`shared_ptr`を使用して**この**は既存のものから区別され`shared_ptr`所有者で、参照が無効です。 または複数回削除するオブジェクトが発生する可能性があります。

コンストラクター、デストラクター、および代入演算子は、偶発的な誤用を防ぐために保護されています。 テンプレート引数の型*Ty*派生クラスの型でなければなりません。

使用方法の例については、「[enable_shared_from_this::shared_from_this](#shared_from_this)」をご覧ください。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<memory>

**名前空間:** std

## <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this

インスタンスの所有権を既存の `shared_ptr` 所有者と共有する `shared_ptr` を生成します。

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Remarks

基底クラス `enable_shared_from_this` からオブジェクトを派生すると、`shared_from_this` テンプレート メンバー関数は、このインスタンスの所有権を既存の `shared_ptr` 所有者と共有する [shared_ptr クラス](../standard-library/shared-ptr-class.md)のオブジェクトを返します。 それ以外の場合、新規に作成する場合`shared_ptr`から**この**は既存のものから区別され`shared_ptr`所有者で、参照が無効です。 または複数回削除するオブジェクトが発生する可能性があります。 `shared_ptr` オブジェクトによってまだ所有されていないインスタンスで `shared_from_this` を呼び出した場合の動作は未定義です。

### <a name="example"></a>例

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="see-also"></a>関連項目

[enable_shared_from_this::shared_from_this](#shared_from_this)<br/>
[shared_ptr クラス](../standard-library/shared-ptr-class.md)<br/>