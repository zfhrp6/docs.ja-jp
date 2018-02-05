---
title: "方法: ConcurrentDictionary の項目を追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4ef7c8050b26cffeed03cc394193116f8f6797a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a><span data-ttu-id="1ddd7-102">方法: ConcurrentDictionary の項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="1ddd7-102">How to: Add and Remove Items from a ConcurrentDictionary</span></span>
<span data-ttu-id="1ddd7-103">この例では、<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> の項目を追加、取得、更新、削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-103">This example shows how to add, retrieve, update, and remove items from a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1ddd7-104">このコレクション クラスは、スレッド セーフな実装です。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-104">This collection class is a thread-safe implementation.</span></span> <span data-ttu-id="1ddd7-105">同時に複数のスレッドが要素へのアクセスを試みる可能性がある場合は常に、このクラスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-105">We recommend that you use it whenever multiple threads might be attempting to access the elements concurrently.</span></span>  
  
 <span data-ttu-id="1ddd7-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> では、コードが事前にキーの存在を調べなくてもデータを追加または削除できるようにする便利なメソッドが提供されています。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> provides several convenience methods that make it unnecessary for code to first check whether a key exists before it attempts to add or remove data.</span></span> <span data-ttu-id="1ddd7-107">次の表では、これらのメソッドとそれを使用する状況を示します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-107">The following table lists these convenience methods and describes when to use them.</span></span>  
  
|<span data-ttu-id="1ddd7-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="1ddd7-108">Method</span></span>|<span data-ttu-id="1ddd7-109">使用する状況</span><span class="sxs-lookup"><span data-stu-id="1ddd7-109">Use when…</span></span>|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|<span data-ttu-id="1ddd7-110">指定したキーで新しい値を追加し、キーが既に存在する場合は値を置換します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-110">You want to add a new value for a specified key and, if the key already exists, you want to replace its value.</span></span>|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|<span data-ttu-id="1ddd7-111">指定したキーの既存の値を取得し、キーが存在しない場合はキー/値ペアを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-111">You want to retrieve the existing value for a specified key and, if the key does not exist, you want to specify a key/value pair.</span></span>|  
|<span data-ttu-id="1ddd7-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span><span class="sxs-lookup"><span data-stu-id="1ddd7-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span></span>|<span data-ttu-id="1ddd7-113">キー/値ペアを追加、取得、更新、または削除し、キーが既に存在するか、他の何らかの理由で操作が失敗する場合は、代わりの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-113">You want to add, get, update, or remove a key/value pair, and, if the key already exists or the attempt fails for any other reason, you want to take some alternative action.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1ddd7-114">例</span><span class="sxs-lookup"><span data-stu-id="1ddd7-114">Example</span></span>  
 <span data-ttu-id="1ddd7-115">次の例では、同時に 2 つの <xref:System.Threading.Tasks.Task> インスタンスを使用して複数の要素を <xref:System.Collections.Concurrent.ConcurrentDictionary%602> に追加し、要素が正常に追加されたことを示すためにすべてのコンテンツを出力します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-115">The following example uses two <xref:System.Threading.Tasks.Task> instances to add some elements to a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> concurrently, and then outputs all of the contents to show that the elements were added successfully.</span></span> <span data-ttu-id="1ddd7-116">また、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> の各メソッドを使用して、コレクションの項目を追加、更新、および取得する例も示しています。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-116">The example also shows how to use the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to add, update, and retrieve  items from the collection.</span></span>  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <span data-ttu-id="1ddd7-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> はマルチスレッド シナリオ向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> is designed for multithreaded scenarios.</span></span> <span data-ttu-id="1ddd7-118">コレクションの項目を追加または削除するために、コードでロックを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-118">You do not have to use locks in your code to add or remove items from the collection.</span></span> <span data-ttu-id="1ddd7-119">ただし、あるスレッドが値を取得した直後に、別のスレッドが同じキーと新しい値を指定してコレクションを更新する可能性が常にあります。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-119">However, it is always possible for one thread to retrieve a value, and another thread to immediately update the collection by giving the same key a new value.</span></span>  
  
 <span data-ttu-id="1ddd7-120">また、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> のメソッドはすべてスレッド セーフですが、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> や <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> などの一部のメソッドはアトミックではありません。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-120">Also, although all methods of <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are thread-safe, not all methods are atomic, specifically <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span></span> <span data-ttu-id="1ddd7-121">これらのメソッドに渡されるユーザー デリゲートは、ディクショナリの内部ロックの外側で呼び出されます </span><span class="sxs-lookup"><span data-stu-id="1ddd7-121">The user delegate that is passed to these methods is invoked outside of the dictionary's internal lock.</span></span> <span data-ttu-id="1ddd7-122">(これは、不明なコードがすべてのスレッドをブロックするのを防ぐために行われます)。そのため、次のような一連のイベントが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-122">(This is done to prevent unknown code from blocking all threads.) Therefore it is possible for this sequence of events to occur:</span></span>  
  
 <span data-ttu-id="1ddd7-123">1\) threadA が <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> を呼び出しましたが、項目が見つからないため、valueFactory デリゲートを呼び出すことにより新しい項目を作成して追加します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-123">1\) threadA calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, finds no item and creates a new item to Add by invoking the valueFactory delegate.</span></span>  
  
 <span data-ttu-id="1ddd7-124">2\) threadB が同時に <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> を呼び出します。その valueFactory デリゲートが呼び出され、threadA より前に内部ロックに到達し、新しいキー/値ペアをディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-124">2\) threadB calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> concurrently, its valueFactory delegate is invoked and it arrives at the internal lock before threadA, and so its new key-value pair is added to the dictionary.</span></span>  
  
 <span data-ttu-id="1ddd7-125">3\) threadA のユーザー デリゲートが完了し、スレッドはロックに到達しますが、項目が既に存在することを検出します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-125">3\) threadA's user delegate completes, and the thread arrives at the lock, but now sees that the item exists already</span></span>  
  
 <span data-ttu-id="1ddd7-126">4\) threadA は "Get" を実行し、threadB によって前に追加されたデータを返します。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-126">4\) threadA performs a "Get", and returns the data that was previously added by threadB.</span></span>  
  
 <span data-ttu-id="1ddd7-127">したがって、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> によって返されるデータが、スレッドの valueFactory によって作成された同じデータであることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-127">Therefore, it is not guaranteed that the data that is returned by <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> is the same data that was created by the thread's valueFactory.</span></span> <span data-ttu-id="1ddd7-128"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> を呼び出したときも、同様の一連のイベントが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1ddd7-128">A similar sequence of events can occur when <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ddd7-129">参照</span><span class="sxs-lookup"><span data-stu-id="1ddd7-129">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="1ddd7-130">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="1ddd7-130">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
