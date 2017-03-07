---
title: "スレッド セーフなコレクションを使用する状況"
description: "スレッド セーフなコレクションを使用する状況"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a2a42d44-f6a5-4f16-9000-026221d66349
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b0b88a85cb4048849464381656a30e8c8ea694d8
ms.lasthandoff: 03/02/2017

---

# <a name="when-to-use-a-thread-safe-collection"></a>スレッド セーフなコレクションを使用する状況

`ConcurrentQueue`、`ConcurrentStack`、`ConcurrentDictionary`、`ConcurrentBag` と `BlockingCollection` コレクション型は、マルチ スレッドの追加および削除の操作をサポートするために、特別に設計されています。 スレッド セーフを確保するために、これらの新しい型では、さまざまな種類の効率的なロック同期機構とロック制御の不要な同期機構が使用されます。 同期を行うと、操作にオーバーヘッドが追加されます。 オーバーヘッドの量は、使用する同期の種類、実行する操作の種類、およびその他の要因 (コレクションに同時にアクセスしようとするスレッドの数など) によって異なります。

一部のシナリオでは、同期のオーバーヘッドがほとんどなく、外部ロックで保護されるスレッド セーフでない同等の型よりもマルチスレッド型の方が、パフォーマンスとスケーラビリティが大幅に向上することがあります。 その他のシナリオでは、オーバーヘッドが原因で、スレッド セーフな型のパフォーマンスとスケーラビリティが、外部からロックされるスレッド セーフでないバージョンの型と同等かそれ以下になることもあります。

以下のセクションでは、スレッド セーフなコレクションと、読み取り操作および書き込み操作でユーザー指定のロックを使用するスレッド セーフでない同等のコレクションの使い分けに関する一般的なガイダンスを示します。 パフォーマンスはさまざまな要因に左右されるため、このガイダンスは特定の状況には沿っておらず、すべての状況で有効であるとは限りません。 パフォーマンスが重要な場合、使用するコレクション型を判断する最適な方法は、代表的なコンピューター構成および負荷に基づいてパフォーマンスを計測することです。 このドキュメントでは、次の用語が使用されています。

*純粋プロデューサー/コンシューマー シナリオ:* 任意のスレッドで、要素の追加または削除のいずれかが実行されますが、両方は実行されません。

*混合プロデューサー/コンシューマー シナリオ:* 任意のスレッドで、要素を追加および削除の両方が実行されます。

*高速化:* 同じシナリオで別の型と比較してアルゴリズムのパフォーマンスが向上することです。

*スケーラビリティ:* コンピューターのコア数に比例したパフォーマンスの向上。 スケーリングするアルゴリズムのパフォーマンスは、コア数が&2; の場合よりも&8; の場合の方が向上します。

## <a name="concurrentqueuelttgt-vs-queuelttgt"></a>ConcurrentQueue&lt;T&gt; 対 Queue&lt;T&gt;

純粋プロデューサー/コンシューマー シナリオでは、各要素の処理時間がとても短い (命令が少ない) 場合、[System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) は、外部ロックを使用する [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) よりも若干優れたパフォーマンスを提供します。 このシナリオでは、キューへの配置とキューからの取り出しをそれぞれ専用のスレッドが実行している場合に、`ConcurrentQueue<T>` のパフォーマンスが最大限に引き出されます。 この規則を強制していない場合、`Queue<T>` は、複数のコアを持つコンピューター上の `ConcurrentQueue<T>` よりも若干向上する場合があります。 

処理時間が 500 FLOPS (浮動小数点演算) 以上の場合、2 つのスレッドを使用する規則は `ConcurrentQueue<T>` に適用されません。この型でとても優れたスケーラビリティが実現します。 `Queue<T>` は、このシナリオではスケーラビリティの点で劣ります。

混合プロデューサー/コンシューマー シナリオでは、処理時間がとても短い場合、外部ロックを使用する `Queue<T>` のスケーラビリティは `ConcurrentQueue<T>` よりも優れています。 ただし、処理時間が約 500 FLOPS 以上の場合、`ConcurrentQueue<T>` の方がスケーラビリティに優れます。

## <a name="concurrentstack-vs-stack"></a>ConcurrentStack 対 Stack

純粋プロデューサー/コンシューマー シナリオでは、処理時間が非常に短い場合、プッシュとポップをそれぞれ専用のスレッドが実行しているときは、[System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) および外部ロックを使用する [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) のパフォーマンスはほぼ同じであると考えられます。 ただし、スレッド数が増えると、競合が増えることで両方の型のパフォーマンスが低下し、`Stack<T>` の方が `ConcurrentStack<T>` よりも優れたパフォーマンスを示すことがあります。 処理時間が約 500 FLOPS 以上の場合は、両方の型がほぼ同じスケーラビリティを示します。 

混合プロデューサー/コンシューマー シナリオでは、ワークロードの大小にかかわらず、`ConcurrentStack<T>` の方が高速です。

`PushRange` と `TryPopRange` を使用すると、アクセス時間が大幅に短縮される可能性があります。

## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary 対 Dictionary

一般に、複数のスレッドから同時にキーまたは値を追加および更新している任意のシナリオでは、[System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) を使用します。 更新を頻繁に行い、読み取りは比較的少ないシナリオでは、通常、`ConcurrentDictionary<TKey, TValue>` には大きな利点はありません。 読み取りも更新も多いシナリオでは、通常、コンピューターに任意の数のコアを備えられる場合は `ConcurrentDictionary<TKey, TValue>` の方が大幅に高速です。

更新を頻繁に行うシナリオでは、`ConcurrentDictionary<TKey, TValue>` で同時実行の程度を上げて、コンピューターのコア数が多いほどパフォーマンスが向上するかどうかを計測できます。 同時実行レベルを変更する場合、グローバル操作はできるだけ避けてください。

キーまたは値の読み取りのみを行う場合、ディクショナリがスレッドによって変更されないときは同期が不要なため、[System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) の方が高速です。

## <a name="concurrentbag"></a>ConcurrentBag

純粋プロデューサー/コンシューマー シナリオでは、[System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) は、その他の同時実行コレクション型よりもパフォーマンスの点で劣ると考えられます。

混合プロデューサー/コンシューマー シナリオでは、通常、ワークロードの大小にかかわらず、`ConcurrentBag<T>` は他の同時実行コレクション型よりもはるかに高速でスケーラビリティに優れます。

## <a name="blockingcollection"></a>BlockingCollection

境界ブロッキング セマンティクスが必要な場合は、[System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) の方がカスタム実装よりもパフォーマンスの点で優れると考えられます。 この型では、高度なキャンセル、列挙、および例外処理もサポートされます。

## <a name="see-also"></a>関連項目

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[スレッドセーフなコレクション](index.md)

