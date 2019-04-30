---
title: error_code クラス
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: f4d0bc2c2922374d27bba3c0693e50f7930dbe67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413698"
---
# <a name="errorcode-class"></a>error_code クラス

実装固有の低レベルなシステム エラーを表します。

## <a name="syntax"></a>構文

```cpp
class error_code;
```

## <a name="remarks"></a>Remarks

`error_code` クラス型のオブジェクトは、エラー コード値を格納するほか、レポートされた低レベルのシステム エラーを説明するエラー コードの[カテゴリ](../standard-library/error-category-class.md)を表すオブジェクトを指すポインターも格納します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[error_code](#error_code)|`error_code` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[value_type](#value_type)|格納されたエラー コード値を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[assign](#assign)|エラー コードにエラー コード値とカテゴリを割り当てます。|
|[category](#category)|エラー カテゴリを返します。|
|[clear](#clear)|エラー コード値とカテゴリをクリアします。|
|[default_error_condition](#default_error_condition)|既定のエラー条件を返します。|
|[message](#message)|エラー コードの名前を返します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator==](#op_eq_eq)|`error_code` オブジェクト間の同等性をテストします。|
|[operator!=](#op_neq)|`error_code` オブジェクト間の不等性をテストします。|
|[operator<](#op_lt)|`error_code` オブジェクトが比較のために渡される `error_code` オブジェクトより小さいかどうかをテストします。|
|[operator=](#op_eq)|`error_code` オブジェクトに新しい列挙値を代入します。|
|[operator bool](#op_bool)|`error_code` 型の変数をキャストします。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<system_error>

**名前空間:** std

## <a name="assign"></a>  error_code::assign

エラー コードにエラー コード値とカテゴリを割り当てます。

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*val*|`error_code` に格納するエラー コード値。|
|*_Cat*|`error_code` に格納するエラー カテゴリ。|

### <a name="remarks"></a>Remarks

メンバー関数のストア*val*エラー コード値とへのポインターとして *_Cat*します。

## <a name="category"></a>  error_code::category

エラー カテゴリを返します。

```cpp
const error_category& category() const;
```

### <a name="remarks"></a>Remarks

## <a name="clear"></a>  error_code::clear

エラー コード値とカテゴリをクリアします。

```cpp
clear();
```

### <a name="remarks"></a>Remarks

このメンバー関数はゼロ エラー コード値と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。

## <a name="default_error_condition"></a>  error_code::default_error_condition

既定のエラー条件を返します。

```cpp
error_condition default_error_condition() const;
```

### <a name="return-value"></a>戻り値

[default_error_condition](../standard-library/error-category-class.md#default_error_condition) で指定された [error_condition](../standard-library/error-condition-class.md)。

### <a name="remarks"></a>Remarks

このメンバー関数は `category().default_error_condition(value())` を返します。

## <a name="error_code"></a>  error_code::error_code

`error_code` 型のオブジェクトを構築します。

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*val*|`error_code` に格納するエラー コード値。|
|*_Cat*|`error_code` に格納するエラー カテゴリ。|
|*_Errcode*|`error_code` に格納する列挙値。|

### <a name="remarks"></a>Remarks

最初のコンストラクターはゼロ エラー コード値と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。

2 番目のコンス トラクター ストア*val*エラー コード値とへのポインターとして[error_category](../standard-library/error-category-class.md)します。

3 番目のコンストラクターは、エラー コード値としての `(value_type)_Errcode` と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。

## <a name="message"></a>  error_code::message

エラー コードの名前を返します。

```cpp
string message() const;
```

### <a name="return-value"></a>戻り値

エラー コードの名前を表す `string`。

### <a name="remarks"></a>Remarks

このメンバー関数は `category().message(value())` を返します。

## <a name="op_eq_eq"></a>  error_code::operator==

`error_code` オブジェクト間の同等性をテストします。

```cpp
bool operator==(const error_code& right) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*right*|等しいかどうかをテストするオブジェクト。|

### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は **true**、オブジェクトが等しくない場合は **false**。

### <a name="remarks"></a>Remarks

このメンバー演算子は、 `category() == right.category() && value == right.value()`を返します。

## <a name="op_neq"></a>  error_code::operator!=

`error_code` オブジェクト間の不等性をテストします。

```cpp
bool operator!=(const error_code& right) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*right*|不等性をテストするオブジェクト。|

### <a name="return-value"></a>戻り値

**true**場合、`error_code`オブジェクトが等しく、`error_code`で渡されるオブジェクト*右*。 そうしないと**false**します。

### <a name="remarks"></a>Remarks

このメンバー演算子は、 `!(*this == right)`を返します。

## <a name="op_lt"></a>  error_code::operator&lt;

`error_code` オブジェクトが比較のために渡される `error_code` オブジェクトより小さいかどうかをテストします。

```cpp
bool operator<(const error_code& right) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*right*|比較する error_code オブジェクト。|

### <a name="return-value"></a>戻り値

`error_code` オブジェクトが、比較対象として渡された `error_code` より小さい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このメンバー演算子は、 `category() < right.category() || category() == right.category() && value < right.value()`を返します。

## <a name="op_eq"></a>  error_code::operator=

`error_code` オブジェクトに新しい列挙値を代入します。

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*_Errcode*|`error_code` オブジェクトに代入する列挙値。|

### <a name="return-value"></a>戻り値

メンバー関数によって新しい列挙値が代入される `error_code` オブジェクトへの参照。

### <a name="remarks"></a>Remarks

このメンバー演算子は、エラー コード値としての `(value_type)_Errcode` と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。 `*this` を返します。

## <a name="op_bool"></a>  error_code::operator bool

`error_code` 型の変数をキャストします。

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>戻り値

`error_code` オブジェクトのブール値。

### <a name="remarks"></a>Remarks

演算子に変換できる値を返します**true**場合にのみ[値](#value)0 と等しくないです。 戻り値の型にのみ変換可能**bool**ではなく、`void *`またはその他の既知のスカラー型。

## <a name="value"></a>  error_code::value

格納されたエラー コード値を返します。

```cpp
value_type value() const;
```

### <a name="return-value"></a>戻り値

[value_type](#value_type) 型の格納されたエラー コード値。

### <a name="remarks"></a>Remarks

## <a name="value_type"></a>  error_code::value_type

格納されたエラー コード値を表す型。

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Remarks

この型定義のシノニムは、 **int**します。

## <a name="see-also"></a>関連項目

[error_category クラス](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
