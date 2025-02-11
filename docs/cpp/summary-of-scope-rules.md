---
title: スコープ規則の概要
ms.date: 11/04/2016
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
ms.openlocfilehash: af708fd72904fb775ff1088948972bec159816c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266908"
---
# <a name="summary-of-scope-rules"></a>スコープ規則の概要

名前の使用はスコープ内で明確である必要があります (オーバーロードが決定される段階まで)。 名前が関数を表している場合、関数はパラメーターの数と型に対し明確でなければなりません。 名前のあいまいさのないままの場合[メンバー アクセス](../cpp/member-access-control-cpp.md)規則が適用されます。

## <a name="constructor-initializers"></a>Constructor Initializers (コンストラクター初期化子)

[コンス トラクター初期化子](constructors-cpp.md#member_init_list)を指定されているコンス トラクターの最も外側のブロックのスコープで評価されます。 したがって、初期化子は、コンストラクターのパラメーター名を使用できます。

## <a name="global-names"></a>Global Names (グローバルな名前)

オブジェクト、関数、または列挙子の名前が関数やクラスの外側に記述されているか、またはグローバル スコープの単項演算子 (`::`) が先頭に付加されており、以下のいずれかの二項演算子と共に使用されていない場合、その名前はグローバルと見なされます。

- スコープ解決 (`::`)

- オブジェクトと参照のメンバー選択 (**.**)

- ポインターのメンバー選択 (**->**)

## <a name="qualified-names"></a>修飾名

バイナリ スコープ解決演算子 (`::`) と共に使用される名前は、"修飾名" と呼ばれます。 バイナリ スコープ解決演算子の後ろに指定される名前は、演算子の左側で指定されたクラスのメンバーまたはその基底クラスのメンバーである必要があります。

メンバー選択演算子の後に指定した名前 (**します。** または**->**) 演算子の左側またはその基底クラスのメンバーで指定されたオブジェクトのクラス型のメンバーである必要があります。 メンバー選択演算子の右辺に指定した名前 (**->**) オブジェクトを指定できますも別のクラス型の条件の左側にある**->** クラス オブジェクトとクラスがオーバー ロードされたメンバー選択演算子を定義すること (**->**) その他のいくつかのクラス型へのポインターに評価されます。 (詳細についてはこのプロビジョニング[クラス メンバーへのアクセス](../cpp/member-access.md))。

コンパイラは、次の順序で名前を検索し、名前が見つかると検索を停止します。

1. 名前が関数内で使用されている場合は現在のブロック スコープを、それ以外の場合はグローバル スコープを検索する。

1. 現在のブロックを囲む各ブロックを外側へ、(関数のパラメーターが含まれる) 最も外側の関数スコープまで検索する。

1. 名前がメンバー関数内で使用されている場合は、そのクラスのスコープで名前を検索する。

1. そのクラスの基底クラスで名前を検索する。

1. 入れ子の外側のクラス スコープ (存在する場合) とその基底クラスを検索する。 最も外側を囲むクラス スコープが検索されるまで検索を続行する。

1. グローバル スコープを検索する。

ただし、この検索順序は、次のように変更できます。

1. `::` の後ろの名前については、グローバル スコープから検索を開始する。

1. 後ろの名前、**クラス**、**構造体**、および**共用体**キーワードだけを検索するコンパイラを強制する**クラス**、 **構造体**、または**共用体**名。

1. スコープ解決演算子の左側にある名前 (`::`) のみを指定できます**クラス**、**構造体**、**名前空間**、または**union**名。

名前が非静的メンバーを参照しているにもかかわらず、静的メンバー関数で使用されている場合は、エラー メッセージが生成されます。 同様に、名前が外側のクラスの非静的メンバーを指す場合、エラー メッセージが生成含まれているクラスは、それを囲むクラスを持たないため**この**ポインター。

## <a name="function-parameter-names"></a>関数のパラメーター名

関数定義内の関数のパラメーター名は、関数本体の最も外側のブロックのスコープ内にあると見なされます。 したがって、それらの引数名はローカル名であり、関数が終了するとスコープ外に出ます。

関数宣言 (プロトタイプ) 内の関数のパラメーター名はローカル スコープにあり、宣言の終了時にスコープ外に出ます。

既定のパラメーターは、上記で説明したとおり、それらを既定とするパラメーターのスコープ内にあります。 ただし、ローカル変数や非静的クラス メンバーにはアクセスできません。 既定のパラメーターは、関数呼び出しの時点で評価されますが、関数宣言の元のスコープで評価されます。 したがって、メンバー関数の既定のパラメーターは、常にクラス スコープで評価されます。

## <a name="see-also"></a>関連項目

[継承](../cpp/inheritance-cpp.md)