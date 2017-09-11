---
title: "方法: パイプラインでブロッキング コレクションの配列を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8dda929df8e3de907c228bbef85749cba5cabc25
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="95061-102">方法: パイプラインでブロッキング コレクションの配列を使用する</span><span class="sxs-lookup"><span data-stu-id="95061-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="95061-103">次の例は、<xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> や <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> などの静的メソッドで <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> オブジェクトの配列を使用し、コンポーネント間の高速で柔軟なデータ転送を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="95061-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95061-104">例</span><span class="sxs-lookup"><span data-stu-id="95061-104">Example</span></span>  
 <span data-ttu-id="95061-105">次の例では、各オブジェクトが同時にデータを入力コレクションから取得し、変換して、出力コレクションに渡す、基本的なパイプラインの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="95061-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 <span data-ttu-id="95061-106">[!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)] [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]</span><span class="sxs-lookup"><span data-stu-id="95061-106">[!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)] [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95061-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="95061-107">See Also</span></span>  
 <span data-ttu-id="95061-108"><xref:System.Collections.Concurrent?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="95061-108"><xref:System.Collections.Concurrent?displayProperty=fullName></span></span>   
 [<span data-ttu-id="95061-109">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="95061-109">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

