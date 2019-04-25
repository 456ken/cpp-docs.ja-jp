---
title: file_status クラス
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 81ce4ecc1673087db8e985f94e297798dd712a6e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160018"
---
# <a name="filestatus-class"></a>file_status クラス

[file_type](../standard-library/filesystem-enumerations.md#file_type) とファイルの [perms](../standard-library/filesystem-enumerations.md#perms) をラップします。

## <a name="syntax"></a>構文

```cpp
class file_status;
```

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[file_status](#file_status)|用のラッパーを構築します[file_type](../standard-library/filesystem-enumerations.md#file_type)とファイル[perms](../standard-library/filesystem-enumerations.md#perms)します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[type](#type)|`file_type` を取得または設定します。|
|[permissions](#permissions)|ファイルのアクセス許可を取得または設定します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_as)|この既定のメンバー代入演算子は想定どおりに動作します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<filesystem >

**Namespace:** std::experimental::filesystem、std::experimental::filesystem

## <a name="file_status"></a> file_status::file_status

用のラッパーを構築します[file_type](../standard-library/filesystem-enumerations.md#file_type)とファイル[perms](../standard-library/filesystem-enumerations.md#perms)します。

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>パラメーター

*ftype*<br/>
指定された`file_type`、既定値は`file_type::none`します。

*マスク*<br/>
指定したファイル`perms`、既定値は`perms::unknown`します。

*file_status*<br/>
格納されているオブジェクト。

## <a name="op_as"></a> file_status::operator =

この既定のメンバー代入演算子は想定どおりに動作します。

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>パラメーター

*file_status*<br/>
[File_status](../standard-library/file-status-class.md)にコピーされる、`file_status`します。

## <a name="type"></a> 型

`file_type` を取得または設定します。

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>パラメーター

*ftype*<br/>
`file_type` と指定します。

## <a name="permissions"></a> アクセス許可

ファイルのアクセス許可を取得または設定します。

Setter を使用してファイルを`readonly`または削除、`readonly`属性。

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>パラメーター

*マスク*<br/>
`perms` と指定します。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)<br/>
[path クラス](../standard-library/path-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
