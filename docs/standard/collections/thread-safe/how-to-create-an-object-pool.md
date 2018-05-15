---
title: '方法: ConcurrentBag を使用してオブジェクト プールを作成する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9239a38d1970a052567f111b57be2b6596f1e5f1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="9bc4c-102">方法: ConcurrentBag を使用してオブジェクト プールを作成する</span><span class="sxs-lookup"><span data-stu-id="9bc4c-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="9bc4c-103">この例では、ConcurrentBag を使用してオブジェクト プールを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="9bc4c-104">オブジェクト プールは、クラスの複数のインスタンスが必要であり、クラスの作成または破棄に大きなコストがかかる状況で、アプリケーションのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="9bc4c-105">クライアント プログラムが新しいオブジェクトを要求すると、オブジェクト プールは最初に既に作成されてプールに返されているオブジェクトを提供しようとします。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="9bc4c-106">使用できるオブジェクトがない場合にのみ、新しいオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="9bc4c-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> は、高速の挿入と削除をサポートし、同じスレッドが項目の追加と削除の両方を行うときは特に高速であるため、オブジェクトの格納に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="9bc4c-108">この例は、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> を中心に構築するようにさらに拡張できます。これは、<xref:System.Collections.Concurrent.ConcurrentQueue%601> や <xref:System.Collections.Concurrent.ConcurrentStack%601> と同じようにバッグ データの構造を実装します。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc4c-109">例</span><span class="sxs-lookup"><span data-stu-id="9bc4c-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc4c-110">参照</span><span class="sxs-lookup"><span data-stu-id="9bc4c-110">See Also</span></span>  
 [<span data-ttu-id="9bc4c-111">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="9bc4c-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
