---
title: '方法: Parallel_invoke を使用して並列並べ替えルーチンを記述するには'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 329cf275f283ba7b57276d06e909905c9a900697
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252933"
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>方法: Parallel_invoke を使用して並列並べ替えルーチンを記述するには

このドキュメントは、使用する方法を説明します、 [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)バイトニック ソート アルゴリズムのパフォーマンスを向上させるアルゴリズム。 バイトニック ソート アルゴリズムでは、入力シーケンスを、より小さな並べ替え済みのパーティションへと再帰的に分割します。 各パーティションの操作は他のすべての操作から独立しているため、バイトニック ソート アルゴリズムは並列的に実行することができます。

バイトニック ソートの例に示しますが、*ソーティング ネットワーク*入力シーケンスのすべての組み合わせを並べ替えますが、この例は、シーケンスの長さが 2 の累乗を並べ替えます。

> [!NOTE]
>  この例では、例を示す目的で、並列並べ替えルーチンを使用します。 PPL では、組み込みの並べ替えアルゴリズムを使用することもできます: [:parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)、 [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)、および[concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)します。 詳細については、次を参照してください。[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)します。

##  <a name="top"></a> セクション

ここでは、次のタスクについて説明します。

- [バイトニック ソートを逐次的に実行します。](#serial)

- [バイトニック ソートを実行する parallel_invoke を使用して並列で](#parallel)

##  <a name="serial"></a> バイトニック ソートを逐次的に実行します。

次の例は、逐次的なバイトニック ソート アルゴリズムを示しています。 `bitonic_sort` 関数は、シーケンスを 2 つのパーティションに分割し、一方のパーティションは昇順に、もう一方のパーティションは降順に並べ替えた後、その結果をマージします。 この関数は、自分自身を 2 回再帰的に呼び出して、それぞれのパーティションを並べ替えます。

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[トップ](#top)]

##  <a name="parallel"></a> バイトニック ソートを実行する parallel_invoke を使用して並列で

ここでは、`parallel_invoke` アルゴリズムを使用して、バイトニック ソート アルゴリズムを並列に実行する方法について説明します。

### <a name="procedures"></a>手順

##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>バイトニック ソート アルゴリズムを並列実行するには

1. ヘッダー ファイル ppl.h の `#include` ディレクティブを追加します。

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. `using` 名前空間の `concurrency` ディレクティブを追加します。

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. `parallel_bitonic_mege` という新しい関数を作成します。この関数は、十分な処理量がある場合に、`parallel_invoke` アルゴリズムを使用してシーケンスを並列にマージします。 それ以外の場合は、`bitonic_merge` を呼び出してシーケンスを逐次的にマージします。

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 前の手順と似たプロセスを実行します (`bitonic_sort` 関数を除く)。

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. 配列を昇順に並べ替える `parallel_bitonic_sort` 関数のオーバーロードされたバージョンを作成します。

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke` アルゴリズムは、オーバーヘッドを低減するために、一連のタスクの最後のタスクを呼び出し元のコンテキストで実行します。 たとえば、`parallel_bitonic_sort` 関数では、1 つ目のタスクは別のコンテキストで実行され、2 つ目のタスクは呼び出し元のコンテキストで実行されます。

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

以下に示したのは完成したコード例です。逐次実行版と並列実行版の両方のバイトニック ソート アルゴリズムが実行されます。 この例では、それぞれの計算に要する時間もコンソールに出力します。

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

4 つのプロセッサを備えたコンピューターを使用したときのサンプル出力を次に示します。

```Output
serial time: 4353
parallel time: 1248
```

[[トップ](#top)]

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするにコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付ける`parallel-bitonic-sort.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

**cl.exe/EHsc 並列-バイトニック-sort.cpp**

## <a name="robust-programming"></a>信頼性の高いプログラミング

この例では、`parallel_invoke`アルゴリズムの代わりに、 [concurrency::task_group](reference/task-group-class.md)クラスの各タスク グループの有効期間が関数を超える拡張しないためです。 `parallel_invoke` オブジェクトと比べて実行に伴うオーバーヘッドが低く、よりパフォーマンスに優れたコードを記述できるため、できる限り `task group` の使用をお勧めします。

アルゴリズムにもよりますが、並列化によってパフォーマンスの向上が見込めるのは、十分な処理量が存在する場合に限られます。 たとえば、`parallel_bitonic_merge` 関数では、シーケンスに含まれる要素数が 500 未満の場合、逐次実行版の `bitonic_merge` を呼び出すようにしています。 また、処理量に基づいて全体的な並べ替え方法を計画することもできます。 たとえば、次の例に示すように、配列に含まれる項目が 500 未満の場合、逐次実行版のクイック ソート アルゴリズムを使用した方が効率的であることがあります。

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

他の並列アルゴリズムと同様に、必要に応じてコードのプロファイリングおよびチューニングを行うことをお勧めします。

## <a name="see-also"></a>関連項目

[タスクの並列化](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 関数](reference/concurrency-namespace-functions.md#parallel_invoke)
