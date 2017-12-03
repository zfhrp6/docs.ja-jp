---
title: "方法: データ サービスの結果のページングを有効にする (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9156ddbe9482683660524898aa0c6ce3673cd75f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="03c42-102">方法: データ サービスの結果のページングを有効にする (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="03c42-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="03c42-103"> では、データ サービス クエリによって返されるエンティティの数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="03c42-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="03c42-104">ページ制限は、サービスの初期化時に呼び出されるメソッドで定義され、エンティティ セットごとに設定できます。</span><span class="sxs-lookup"><span data-stu-id="03c42-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="03c42-105">ページングが有効である場合、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="03c42-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="03c42-106">詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="03c42-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="03c42-107">このトピックでは、返された `Customers` エンティティ セットおよび `Orders` エンティティ セットのページングを有効にするためにデータ サービスを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03c42-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="03c42-108">このトピックの例では、Northwind サンプル データ サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="03c42-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="03c42-109">このサービスの作成が完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="03c42-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="03c42-110">返された Customer エンティティ セットおよび Orders エンティティ セットのページングを有効化する方法</span><span class="sxs-lookup"><span data-stu-id="03c42-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="03c42-111">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="03c42-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="03c42-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="03c42-112">See Also</span></span>  
 [<span data-ttu-id="03c42-113">遅延コンテンツの読み込み</span><span class="sxs-lookup"><span data-stu-id="03c42-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="03c42-114">方法: ページングされた結果を読み込む</span><span class="sxs-lookup"><span data-stu-id="03c42-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
