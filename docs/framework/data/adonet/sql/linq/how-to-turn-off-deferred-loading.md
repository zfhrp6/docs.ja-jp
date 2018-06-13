---
title: '方法 : 遅延読み込みをオフにする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 279317f10211271fad812068215b08a93e30fbdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358645"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="5d0d3-102">方法 : 遅延読み込みをオフにする</span><span class="sxs-lookup"><span data-stu-id="5d0d3-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="5d0d3-103"><xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定すると、遅延読み込みをオフにできます。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="5d0d3-104">詳細については、次を参照してください。[遅延実行と即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d0d3-105">遅延読み込みは、オブジェクト トラッキングをオフにすると暗黙でオフになります。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="5d0d3-106">詳細については、次を参照してください。[する方法: 読み取り専用として情報を取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d0d3-107">例</span><span class="sxs-lookup"><span data-stu-id="5d0d3-107">Example</span></span>  
 <span data-ttu-id="5d0d3-108"><xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定して、遅延読み込みをオフにする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5d0d3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d0d3-109">See Also</span></span>  
 [<span data-ttu-id="5d0d3-110">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="5d0d3-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="5d0d3-111">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="5d0d3-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
