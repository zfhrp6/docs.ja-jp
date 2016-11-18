---
title: "方法: ForEach を使用して BlockingCollection 内の項目を削除する"
description: "方法: ForEach を使用して BlockingCollection 内の項目を削除する"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f3db5825-b5c9-4e8b-80bc-e11760d9523e
translationtype: Human Translation
ms.sourcegitcommit: c15f2da15c6448cf1c36dea2d5fd53e734bb6608
ms.openlocfilehash: 98a01aaebb209fe80b3c1270295399e5914cbd09

---

# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>方法: ForEach を使用して BlockingCollection 内の項目を削除する

`Take` および `TryTake` メソッドを使用して [BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) から項目を取得するだけでなく、`foreach` ループを使用して、追加が完了してコレクションが空になるまで項目を削除することもできます。 これは、通常の `foreach` ループとは異なり、この列挙子が項目を削除することでソース コレクションを変更するので、変更列挙または消費列挙と呼ばれます。

## <a name="example"></a>例

次の例では、`foreach` ループを使用して `BlockingCollection<T>` のすべての項目を削除する方法を示します。 

```csharp
using System;
using System.Collections.Concurrent;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

class Example
{
   // Limit the collection size to 2000 items at any given time.
   // Set itemsToProduce to > 500 to hit the limit.
   const int upperLimit = 1000;

   // Adjust this number to see how it impacts the producing-consuming pattern.
   const int itemsToProduce = 100;

   static BlockingCollection<long> collection = new BlockingCollection<long>(upperLimit);

   // Variables for diagnostic output only.
   static Stopwatch sw = new Stopwatch();
   static int totalAdditions = 0;

   // Counter for synchronizing producers.
   static int producersStillRunning = 2;

   static void Main()
   {
       // Start the stopwatch.
       sw.Start();

       // Queue the Producer threads. Store in an array
       // for use with ContinueWhenAll
       Task[] producers = new Task[2];
       producers[0] = Task.Run(() => RunProducer("A", 0));
       producers[1] = Task.Run(() => RunProducer("B", itemsToProduce));

       // Create a cleanup task that will call CompleteAdding after
       // all producers are done adding items.
       Task cleanup = Task.Factory.ContinueWhenAll(producers, (p) => collection.CompleteAdding());

       // Queue the Consumer thread. Put this call
       // before Parallel.Invoke to begin consuming as soon as
       // the producers add items.
       Task.Run(() => RunConsumer());

       // Keep the console window open while the
       // consumer thread completes its output.
       Console.ReadKey(true);
   }

   static void RunProducer(string ID, int start)
   {

       int additions = 0;
       for (int i = start; i < start + itemsToProduce; i++)
       {
           // The data that is added to the collection.
           long ticks = sw.ElapsedTicks;

           // Display additions and subtractions.
           Console.WriteLine("{0} adding tick value {1}. item# {2}", ID, ticks, i);

           if(!collection.IsAddingCompleted)
               collection.Add(ticks);

           // Counter for demonstration purposes only.
           additions++;

           // Uncomment this line to
           // slow down the producer threads     ing.
           Thread.SpinWait(100000);
       }

       Interlocked.Add(ref totalAdditions, additions);
       Console.WriteLine("{0} is done adding: {1} items", ID, additions);
   }

   static void RunConsumer()
   {
       // GetConsumingEnumerable returns the enumerator for the
       // underlying collection.
       int subtractions = 0;
       foreach (var item in collection.GetConsumingEnumerable())
       {
           Console.WriteLine("Consuming tick value {0} : item# {1} : current count = {2}",
                   item.ToString("D18"), subtractions++, collection.Count);
       }

       Console.WriteLine("Total added: {0} Total consumed: {1} Current count: {2} ",
                           totalAdditions, subtractions, collection.Count);
       sw.Stop();

       Console.WriteLine("Press any key to exit");
   }
}

```

この例では、消費スレッドの `BlockingCollection<T>.GetConsumingEnumerable` メソッドで `foreach` ループを使用します。各項目は列挙されるとコレクションから削除されます。 `BlockingCollection<T>` はコレクション内の項目の最大数を制限します。 この方法でコレクションを列挙すると、使用できる項目がない場合、またはコレクションが空の場合は、コンシューマー スレッドがブロックされます。 この例では、プロデューサー スレッドによる項目の追加の方が項目の消費より高速なので、ブロックは問題になりません。 

プロデューサー スレッドによって追加されたのと同じ順序で、項目が列挙されるという保証はありません。

変更せずにコレクションを列挙するには、`GetConsumingEnumerable` メソッドを使用しないで `foreach` だけを使用します。 ただし、この種の列挙は特定時点のコレクションのスナップショットを表すことを理解しておくことが重要です。 ループの実行中に同時に他のスレッドが項目を追加または削除する場合、ループはコレクションの実際の状態を表さない可能性があります。

## <a name="see-also"></a>関連項目

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[BlockingCollection の概要](blockingcollection-overview.md)



<!--HONumber=Nov16_HO3-->


