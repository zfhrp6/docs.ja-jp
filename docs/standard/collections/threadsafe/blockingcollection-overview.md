---
title: "BlockingCollection の概要"
description: "BlockingCollection の概要"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a1a867de-53c2-49ca-9a1a-e5770a942724
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 64a01b5e21e012dfaae07a02f5fb27932be9cf98

---

# <a name="blockingcollection-overview"></a>BlockingCollection の概要

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) は、次の機能を提供するスレッド セーフなコレクション クラスです。

*   Producer-Consumer パターンの実装。

*   コレクションの項目のスレッド セーフな追加と削除。

*   最大容量 (オプション)。

*   コレクションが空またはいっぱいになったときにブロックする挿入操作と削除操作。

*   ブロックせずに実行されるか、指定された時間が経過するまでブロックする、挿入および削除の "試行" 操作。

*   [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) を実装する任意のコレクション型のカプセル化。

*   キャンセル トークンを使用したキャンセル。

*   `foreach` を使用した 2 種類の列挙。 

    1. 読み取り専用の列挙。
    
    2. 列挙された項目を削除する列挙。
    
## <a name="bounding-and-blocking-support"></a>境界とブロッキングのサポート 

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) は境界とブロッキングをサポートします。 境界は、コレクションの最大容量を設定できることを意味します。 境界を使用すると、メモリ内のコレクションの最大サイズを制御し、producer スレッドが consumer スレッドよりも先に進行しすぎるのを防ぐことができます。これは、特定のシナリオで重要になります。

コレクションには、複数のスレッドやタスクが同時に項目を追加できます。コレクションが指定された最大容量に達すると、producer スレッドは項目が削除されるまでブロックします。 複数の cosumer が同時に項目を削除できます。コレクションが空になった場合、consumer スレッドは、producer が項目を追加するまでブロックします。 producer スレッドでは、それ以上項目が追加されないことを示すために、`CompleteAdding` を呼び出すことができます。 consumer では、`IsCompleted` プロパティを監視して、コレクションが空になったときや、それ以上の項目は追加されないことになったときを把握できます。 次の例は、容量の上限が 100 に設定された単純な `BlockingCollection` を示しています。 いくつかの外部条件が true である間、producer タスクはコレクションに項目を追加し、`CompleteAdding` を呼び出します。 consumer タスクは、`IsCompleted` プロパティが true になるまで項目を取得します。

```csharp
// A bounded collection. It can hold no more 
// than 100 items at once.
BlockingCollection<Data> dataItems = new BlockingCollection<Data>(100);


// A simple blocking consumer with no cancellation.
Task.Run(() => 
{
    while (!dataItems.IsCompleted)
    {

        Data data = null;
        // Blocks if number.Count == 0
        // IOE means that Take() was called on a completed collection.
        // Some other thread can call CompleteAdding after we pass the
        // IsCompleted check but before we call Take. 
        // In this example, we can simply catch the exception since the 
        // loop will break on the next iteration.
        try
        {
            data = dataItems.Take();
        }
        catch (InvalidOperationException) { }

        if (data != null)
        {
            Process(data);
        }
    }
    Console.WriteLine("\r\nNo more items to take.");
});

// A simple blocking producer with no cancellation.
Task.Run(() =>
{
    while (moreItemsToAdd)
    {
        Data data = GetData();
        // Blocks if numbers.Count == dataItems.BoundedCapacity
        dataItems.Add(data);
    }
    // Let consumer know we are done.
    dataItems.CompleteAdding();
});
```

コード例全体については、「[方法: BlockingCollection の項目を個別に追加および取得する](how-to-add-and-take-items.md)」を参照してください。

## <a name="timed-blocking-operations"></a>時間制限付きのブロッキング操作

境界のあるコレクションにおける時間制限付きの `TryAdd` 操作および `TryTake` 操作では、メソッドは項目を追加または取得しようと試みます。 項目を使用できる場合、その項目は参照渡しで渡された変数に格納され、メソッドは `true` を返します。 指定されたタイムアウト期間を経過しても項目が取得されない場合、メソッドは `false` を返します。 その後、再びコレクションへのアクセスを試みる前に、他の必要な処理をスレッドで自由に実行できます。 時間制限付きのブロッキング アクセスの例については、「[方法: BlockingCollection の項目を個別に追加および取得する](how-to-add-and-take-items.md)」の 2 番目の例を参照してください。

## <a name="cancelling-add-and-take-operations"></a>追加操作と取得操作の取り消し

追加操作と取得操作は、通常、ループ内で実行されます。 `TryAdd` メソッドまたは `TryTake` メソッドに `CancellationToken` を渡し、各イテレーションでトークンの `IsCancellationRequested` プロパティの値を確認するようにすると、ループを取り消すことができます。 値が `true` である場合は、キャンセル要求に応答するかどうかを決定できます。応答するには、リソースをクリーンアップし、ループを終了します。 次の例は、キャンセル トークンを受け取る `TryAdd` のオーバーロードと、それを使用するコードを示しています。

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="specifying-the-collection-type"></a>コレクションの型の指定

`BlockingCollection<T>;` の作成時には、容量の上限だけでなく、使用するコレクションの型も指定できます。 たとえば、先入れ先出し法 (FIFO) の動作には [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) を指定し、後入れ先出し法 (LIFO) の動作には [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) を指定できます。 [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) インターフェイスを実装する任意のコレクション クラスを使用できます。 `BlockingCollection<T>` の既定のコレクション型は `ConcurrentQueue<T>` です。 次のコード例は、容量が 1000 で、[ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) を使用する文字列の `BlockingCollection<T>` を作成する方法を示しています。

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="ienumerable-support"></a>IEnumerable のサポート

`BlockingCollection<T>` は `GetConsumingEnumerable` メソッドを提供します。これにより、コンシューマーは `foreach` ステートメントを使用して、コレクションが完成するまで (コレクションが空になり、それ以上項目が追加されなくなるまで) 項目を削除できます。 詳細については、「[方法: ForEach を使用して BlockingCollection 内の項目を削除する](how-to-use-foreach-to-remove.md)」を参照してください。

## <a name="using-many-blockingcollections-as-one"></a>多数の BlockingCollection を 1 つとして使用する

consumer が複数のコレクションから同時に項目を取得する必要のあるシナリオでは、`BlockingCollection<T>` の配列を作成し、`TakeFromAny` や `AddToAny` などの静的メソッドを使用できます。これらのメソッドでは、配列内の任意のコレクションを対象に追加または取得の操作を実行できます。 いずれかのコレクションがブロックしている場合、メソッドはすぐに別のコレクションを試します。これは、操作を実行できるコレクションが見つかるまで続行されます。 詳細については、「[方法: パイプラインでブロッキング コレクションの配列を使用する](how-to-use-arrays-of-blockingcollections.md)」を参照してください。

## <a name="see-also"></a>関連項目

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[コレクションとデータ構造体](../index.md)

[スレッドセーフなコレクション](index.md)




<!--HONumber=Nov16_HO3-->


