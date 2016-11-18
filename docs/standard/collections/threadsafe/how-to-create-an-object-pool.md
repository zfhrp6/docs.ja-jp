---
title: "方法: ConcurrentBag を使用してオブジェクト プールを作成する"
description: "方法: ConcurrentBag を使用してオブジェクト プールを作成する"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a6ada1-ee27-423d-b587-82e7cb45361b
translationtype: Human Translation
ms.sourcegitcommit: 2f8dede4c6f679466e8441b29cf778dc46059196
ms.openlocfilehash: 2633a1665e7337cf7d324016a0da6386a777e4a3

---

# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>方法: ConcurrentBag を使用してオブジェクト プールを作成する

この例では、ConcurrentBag を使用してオブジェクト プールを実装する方法を示します。 オブジェクト プールは、クラスの複数のインスタンスが必要であり、クラスの作成または破棄に大きなコストがかかる状況で、アプリケーションのパフォーマンスを向上させることができます。 クライアント プログラムが新しいオブジェクトを要求すると、オブジェクト プールは最初に既に作成されてプールに返されているオブジェクトを提供しようとします。 使用できるオブジェクトがない場合にのみ、新しいオブジェクトが作成されます。 

[ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) は、高速の挿入と削除をサポートし、同じスレッドが項目の追加と削除の両方を行うときは特に高速であるため、オブジェクトの格納に使用されます。 次の例は、[IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) を中心に構築してさらに拡張できます。これは、[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) や [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) と同じようにバッグ データの構造を実装します。

## <a name="example"></a>例

```csharp
using System;
using System.Collections.Concurrent;
using System.Threading;
using System.Threading.Tasks;


namespace ObjectPoolExample
{
    public class ObjectPool<T>
    {
        private ConcurrentBag<T> _objects;
        private Func<T> _objectGenerator;

        public ObjectPool(Func<T> objectGenerator)
        {
            if (objectGenerator == null) throw new ArgumentNullException("objectGenerator");

            _objects = new ConcurrentBag<T>();
            _objectGenerator = objectGenerator;
        }

        public T GetObject()
        {
            T item;
            return _objects.TryTake(out item) ? item : _objectGenerator();
        }

        public void PutObject(T item)
        {
            _objects.Add(item);
        }
    }

    class Program
    {
       static void Main(string[] args)
        {
            CancellationTokenSource cts = new CancellationTokenSource();

            // Create an opportunity for the user to cancel.
            Task.Run(() =>
                {
                    if (Console.ReadKey().KeyChar == 'c' || Console.ReadKey().KeyChar == 'C')
                        cts.Cancel();
                });

            ObjectPool<MyClass> pool = new ObjectPool<MyClass> (() => new MyClass());            

            // Create a high demand for MyClass objects.
            Parallel.For(0, 1000000, (i, loopState) =>
                {
                    MyClass mc = pool.GetObject();
                    Console.CursorLeft = 0;
                    // This is the bottleneck in our application. All threads in this loop
                    // must serialize their access to the static Console class.
                    Console.WriteLine("{0:####.####}", mc.GetValue(i));                 

                    pool.PutObject(mc);
                    if (cts.Token.IsCancellationRequested)
                        loopState.Stop();                 
                });
            Console.WriteLine("Press the Enter key to exit.");
            Console.ReadLine();
            cts.Dispose();
        }
    }

    // A toy class that requires some resources to create.
    // You can experiment here to measure the performance of the
    // object pool vs. ordinary instantiation.
    class MyClass
    {
        public int[] Nums {get; set;}
        public double GetValue(long i)
        {
            return Math.Sqrt(Nums[i]);
        }
        public MyClass()
        {
            Nums = new int[1000000];
            Random rand = new Random();
            for (int i = 0; i < Nums.Length; i++)
                Nums[i] = rand.Next();
        }
    }   
}
```

## <a name="see-also"></a>関連項目

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[スレッドセーフなコレクション](index.md)





<!--HONumber=Nov16_HO3-->


