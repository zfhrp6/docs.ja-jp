---
title: "方法: データ サービスへのアクセスを有効にする (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98584405b0c6a86f424f4bf82e29ea33197dfbeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="b7751-102">方法: データ サービスへのアクセスを有効にする (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="b7751-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="b7751-103">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスによって公開されているリソースに明示的にアクセス権を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7751-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="b7751-104">つまり、新しいデータ サービスを作成した後も、個々のリソースに対し、エンティティ セットとして明示的にアクセスを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7751-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="b7751-105">このトピックの内容が読み取りを有効にする方法を示していて、完了したときに作成される Northwind データ サービスの 5 つのエンティティへの書き込みアクセスを設定、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b7751-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="b7751-106"><xref:System.Data.Services.EntitySetRights> 列挙体は <xref:System.FlagsAttribute> を使用して定義されているので、論理和演算子を使用して 1 つのエンティティ セットに複数のアクセス許可を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b7751-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7751-107">ASP.NET アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b7751-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="b7751-108">運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7751-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="b7751-109">詳細については、次を参照してください。 [NIB: ASP.NET セキュリティ](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)です。</span><span class="sxs-lookup"><span data-stu-id="b7751-109">For more information, see [NIB: ASP.NET Security](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="b7751-110">データ サービスへのアクセスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="b7751-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="b7751-111">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b7751-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="b7751-112">これにより、クライアントから `Orders` および `Order_Details` エンティティ セットへの読み取りおよび書き込みアクセスと、`Customers` エンティティ セットへの読み取り専用アクセスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="b7751-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7751-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7751-113">See Also</span></span>  
 [<span data-ttu-id="b7751-114">方法: IIS で実行されている WCF データ サービスの開発</span><span class="sxs-lookup"><span data-stu-id="b7751-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="b7751-115">データ サービスの構成</span><span class="sxs-lookup"><span data-stu-id="b7751-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
