---
title: output_iterator_tag 構造体
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: cb2a59d2c81e6d7cc80de2714ba86476c5fa837f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370854"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag 構造体

戻り値の型を提供するクラス`iterator_category`出力反復子を表す関数。

## <a name="syntax"></a>構文

構造体 output_iterator_tag {};

## <a name="remarks"></a>Remarks

カテゴリ タグ クラスはアルゴリズムの選択にコンパイル タグとして使用されます。 テンプレート関数は、コンパイル時に最も効率的なアルゴリズムを利用できるように、その反復子引数の最も具体的なカテゴリを見つける必要があります。 `Iterator` 型の反復子ごとに、反復子の動作を表す最も具体的なカテゴリ タグとして `iterator_traits`< `Iterator`> **::iterator_category** を定義する必要があります。

型が同じ**反復子**\< **Iter**> **:::iterator_category**とき`Iter`として使用できるオブジェクトについて説明します、出力反復子。

このタグは、出力反復子には `value_type` または `difference_type` がないため、他の反復子タグと同様、反復子の `value_type` または `difference_type` でパラメーター化されません。

## <a name="example"></a>例

参照してください[iterator_traits](../standard-library/iterator-traits-struct.md)または[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)を使用する方法の例については`iterator_tag`s。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<iterator>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)<br/>
