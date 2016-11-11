---
title: "スレッド セーフなコレクション"
description: "スレッド セーフなコレクション"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 92d5515d-f5d6-4a09-8bbb-31865d678643
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: 421d46585b5d83f5772fa6596ad581c8c6acbf71

---

# <a name="threadsafe-collections"></a>スレッド セーフなコレクション

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間には、スレッド セーフかつスケーラブルないくつかのコレクション クラスが含まれています。 ユーザー コードで同期を追加することなく、複数のスレッドでこのようなコレクションの項目を安全かつ効率的に追加または削除できます。 新しいコードを記述するときに、コレクションが複数のスレッドに同時に書き込みを行う場合は、常に同時実行コレクション クラスを使用します。 共有コレクションの読み取りのみを行う場合は、[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 名前空間のクラスを使用できます。 .NET Framework 1.1 以前のランタイムを対象にする必要がない場合は、[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) のコレクション クラスを使用しないことをお勧めします。

## <a name="finegrained-locking-and-lockfree-mechanisms"></a>粒度の細かいロック機構とロック制御の不要な機構

同時実行コレクション型には、[SpinLock](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinLock)、[SpinWait](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinWait)、[SemaphoreSlim](https://docs.microsoft.com/dotnet/core/api/System.Threading.SemaphoreSlim)、[CountdownEvent](https://docs.microsoft.com/dotnet/core/api/System.Threading.CountdownEvent) などの軽量な同期機構を使用するものもあります。 これらの同期型では、通常、スレッドを実際の `Wait` 状態にする前の短期間にビジー スピンが使用されます。 待機時間が非常に短くなると予測される場合は、スピンを使用すると、負荷がかかるカーネル遷移を伴う待機を行うよりも負荷が格段に小さくなります。 スピンを使用するコレクション クラスでは、この効率性は、複数のスレッドで項目を高速で追加および削除できることを意味します。

[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) および [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) クラスはロックを一切使用しません。 代わりに、インタロック操作によってスレッド セーフを確保します。

> [!NOTE]
> 同時実行コレクション クラスでは [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) がサポートされるので、`IsSynchronized` プロパティと `SyncRoot` プロパティの実装が、これらのプロパティが無関係の場合でも提供されます。 `IsSynchronized` は常に `false` を返し、`SyncRoot` は常に null になります。

次の表は、[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間のコレクション型を示しています。

型 | 説明
---- | -----------
[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) | [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) を実装する任意の型に境界ブロッキング機能を提供します。 詳細については、「[BlockingCollection の概要](blockingcollection-overview.md)」を参照してください。
[ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) | 要素の順序付けられていないコレクションのスレッド セーフな実装。
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) | キーと値のペアのディクショナリのスレッド セーフな実装。
[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) | 先入れ先出し (FIFO: First In First Out) キューのスレッド セーフな実装。
[ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) | 後入れ先出し (LIFO: Last In First Out) スタックのスレッド セーフな実装。
[IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) | `BlockingCollection` で使用するために型が実装する必要があるインターフェイス。

## <a name="thread-synchronization-in-the-net-framework-version-10-and-20-collections"></a>.NET Framework のバージョン 1.0 と 2.0 のコレクションのスレッドの同期

.NET Framework バージョン 1.0 で最初に導入されたコレクションは、[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 名前空間にあります。 一般的に使用される [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) や [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) を含むこのコレクションは、コレクションのスレッド セーフ ラッパーを返す `Synchronized` プロパティを通じてスレッド セーフを確保します。 このラッパーは、すべての追加操作または削除操作でコレクション全体をロックすることで機能します。 したがって、コレクションにアクセスしようとする各スレッドは、ロックを取得する順番を待機する必要があります。 これはスケーラブルではなく、大規模なコレクションの場合はパフォーマンスが大幅に低下するおそれがあります。 また、競合状態を完全に防ぐことはできません。 

.NET Framework バージョン 2.0 で最初に導入されたコレクション クラスは、[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 名前空間にあります。 これには、[List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)、[Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) などが含まれます。 これらのクラスを使用すると、`System.Collections` クラスと比較して、タイプ セーフおよびパフォーマンスが向上します。 ただし、`System.Collections.Generic` コレクション クラスではスレッドの同期は行われません。複数のスレッドで同時に項目を追加または削除する場合は、ユーザー コードですべての同期を行う必要があります。

`System.Collections.Concurrent` のコレクション クラスを使用することをお勧めします。このクラスは、`System.Collections.Generic` コレクション クラスのタイプ セーフを確保するだけでなく、`System.Collections` コレクションよりも効率的で完全なスレッド セーフも確保します。

## <a name="related-topics"></a>関連トピック

タイトル | 説明
----- | -----------
[BlockingCollection の概要](blockingcollection-overview.md) | `BlockingCollection<T>` 型で提供される機能について説明します。
[スレッドセーフなコレクションの使用に適した状況](when-to-use-a-thread-safe-collection.md) | スレッド セーフなコレクションの使用が適している場合について説明します。
[方法: ConcurrentDictionary の項目を追加および削除する](how-to-add-and-remove-items.md) | `ConcurrentDictionary<TKey, TValue>` の要素を追加および削除する方法について説明します。
[方法: BlockingCollection の項目を個別に追加および取得する](how-to-add-and-take-items.md) | 読み取り専用の列挙子を使用せずにブロッキング コレクションの項目を追加および取得する方法について説明します。
[方法: 境界ブロッキング機能をコレクションに追加する](how-to-add-bounding-and-blocking.md ) | 任意のコレクション クラスを `IProducerConsumerCollection<T>;` コレクションの基になるストレージ機構として使用する方法について説明します。
[方法: ForEach を使用して BlockingCollection 内の項目を削除する](how-to-use-foreach-to-remove.md ) | `foreach` を使用してブロッキング コレクションのすべての項目を削除する方法について説明します。
[方法: パイプラインでブロッキング コレクションの配列を使用する](how-to-use-arrays-of-blockingcollections.md) | 複数のブロッキング コレクションを同時に使用してパイプラインを実装する方法について説明します。
[方法: ConcurrentBag を使用してオブジェクト プールを作成する](how-to-create-an-object-pool.md) | 新しいオブジェクトを頻繁に作成する代わりにオブジェクトを再利用できるシナリオで、同時実行バッグを使用してパフォーマンスを向上させる方法について説明します。

## <a name="reference"></a>参照

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)






 





<!--HONumber=Nov16_HO1-->


