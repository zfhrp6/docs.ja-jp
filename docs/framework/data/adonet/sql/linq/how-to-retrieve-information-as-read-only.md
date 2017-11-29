---
title: "方法 : 情報を読み取り専用として取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a9765d8d8330c7ad2a6e8cb25166427cdd9414a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="2fb6b-102">方法 : 情報を読み取り専用として取得する</span><span class="sxs-lookup"><span data-stu-id="2fb6b-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="2fb6b-103">データを変更する予定がない場合は、読み取り専用の結果を取得することでクエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="2fb6b-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="2fb6b-104">読み取り専用の処理を実装するには、<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="2fb6b-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fb6b-105"><xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定すると、<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> が暗黙的に `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="2fb6b-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fb6b-106">例</span><span class="sxs-lookup"><span data-stu-id="2fb6b-106">Example</span></span>  
 <span data-ttu-id="2fb6b-107">次のコード例は、従業員の入社日の読み取り専用コレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="2fb6b-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2fb6b-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fb6b-108">See Also</span></span>  
 [<span data-ttu-id="2fb6b-109">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="2fb6b-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="2fb6b-110">データベースの照会</span><span class="sxs-lookup"><span data-stu-id="2fb6b-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [<span data-ttu-id="2fb6b-111">遅延実行と即時読み込み</span><span class="sxs-lookup"><span data-stu-id="2fb6b-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
