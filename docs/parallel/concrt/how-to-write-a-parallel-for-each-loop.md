---
title: '方法: Parallel_for_each ループを記述します。'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: 19af9be8ef6d9c38a0942e7c85caa0a8bc4e6813
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375562"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>方法: Parallel_for_each ループを記述します。

この例は、使用する方法を示します、 [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)内の素数の数を計算するアルゴリズム、 [std::array](../../standard-library/array-class-stl.md)並列オブジェクト。

## <a name="example"></a>例

次の例では、配列に含まれる素数の数を 2 回計算します。 例を使用して、 [std::for_each](../../standard-library/algorithm-functions.md#for_each)逐次的に数を計算するアルゴリズム。 次に、`parallel_for_each` アルゴリズムを使用して、同じタスクを並列に実行します。 また、それぞれの計算に要する時間もコンソールに出力します。

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

4 つのプロセッサを備えたコンピューターを使用したときのサンプル出力を次に示します。

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするにコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付ける`parallel-count-primes.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

**cl.exe /EHsc parallel-count-primes.cpp**

## <a name="robust-programming"></a>信頼性の高いプログラミング

この例で `parallel_for_each` アルゴリズムに渡すラムダ式では、`InterlockedIncrement` 関数を使用して、ループの反復処理を並列で行い、カウンターを同時にインクリメントします。 `InterlockedIncrement` などの関数を使用して共有リソースへのアクセスを同期化すると、コードのパフォーマンスのボトルネックを示すことができます。 たとえば、ロックフリー同期メカニズムを使用することができます、 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md)共有リソースへの同時アクセスをなくすのクラス。 使用する例については、`combinable`この方法でクラスを参照してください[方法。パフォーマンスを向上させる combinable を使用して](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)します。

## <a name="see-also"></a>関連項目

[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each 関数](reference/concurrency-namespace-functions.md#parallel_for_each)
