---
title: '方法 : 情報を読み取り専用として取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: dd3a510339bca8649f5654d00a9cbdfba156d92c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360701"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="63856-102">方法 : 情報を読み取り専用として取得する</span><span class="sxs-lookup"><span data-stu-id="63856-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="63856-103">データを変更する予定がない場合は、読み取り専用の結果を取得することでクエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="63856-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="63856-104">読み取り専用の処理を実装するには、<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="63856-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63856-105"><xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定すると、<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> が暗黙的に `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="63856-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63856-106">例</span><span class="sxs-lookup"><span data-stu-id="63856-106">Example</span></span>  
 <span data-ttu-id="63856-107">次のコード例は、従業員の入社日の読み取り専用コレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="63856-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="63856-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="63856-108">See Also</span></span>  
 [<span data-ttu-id="63856-109">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="63856-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="63856-110">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="63856-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [<span data-ttu-id="63856-111">遅延読み込みと即時読み込み</span><span class="sxs-lookup"><span data-stu-id="63856-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
