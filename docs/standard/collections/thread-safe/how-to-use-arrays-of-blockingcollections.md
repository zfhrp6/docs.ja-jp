---
title: '方法: パイプラインでブロッキング コレクションの配列を使用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9313f1064534702fdc2d239eb7f0f69a470329e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567771"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="f3e0e-102">方法: パイプラインでブロッキング コレクションの配列を使用する</span><span class="sxs-lookup"><span data-stu-id="f3e0e-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="f3e0e-103">次の例は、<xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> や <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> などの静的メソッドで <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> オブジェクトの配列を使用し、コンポーネント間の高速で柔軟なデータ転送を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f3e0e-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e0e-104">例</span><span class="sxs-lookup"><span data-stu-id="f3e0e-104">Example</span></span>  
 <span data-ttu-id="f3e0e-105">次の例では、各オブジェクトが同時にデータを入力コレクションから取得し、変換して、出力コレクションに渡す、基本的なパイプラインの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="f3e0e-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="f3e0e-106">参照</span><span class="sxs-lookup"><span data-stu-id="f3e0e-106">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="f3e0e-107">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="f3e0e-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
