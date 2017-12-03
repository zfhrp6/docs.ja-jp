---
title: "方法: リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11f01a88e1d276321384f00f3e103322ccaef339
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="dae38-102">方法: リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="dae38-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="dae38-103"> では、<xref:System.Linq.IQueryable%601> インターフェイスを実装するオブジェクトとして公開されているクラスに基づいてデータ モデルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="dae38-103"> enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="dae38-104">詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="dae38-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dae38-105">例</span><span class="sxs-lookup"><span data-stu-id="dae38-105">Example</span></span>  
 <span data-ttu-id="dae38-106">次の例は、`Orders` および `Items` を含むデータ モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="dae38-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="dae38-107">エンティティ コンテナー クラス `OrderItemData` には、<xref:System.Linq.IQueryable%601> インターフェイスを返す 2 つのパブリック メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="dae38-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="dae38-108">これらのインターフェイスは、`Orders` エンティティ型と `Items` エンティティ型のエンティティ セットです。</span><span class="sxs-lookup"><span data-stu-id="dae38-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="dae38-109">`Order` には複数の `Items` を含めることができるので、`Orders` エンティティ型には `Items` オブジェクトのコレクションを返す `Items` ナビゲーション プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="dae38-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="dae38-110">`OrderItemData` エンティティ コンテナー クラスは、<xref:System.Data.Services.DataService%601> データ サービスが派生する `OrderItems` クラスのジェネリック型です。</span><span class="sxs-lookup"><span data-stu-id="dae38-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dae38-111">この例はメモリ内のデータ プロバイダーを示し、変更は現在のオブジェクト インスタンスの外部で永続化されないので、<xref:System.Data.Services.IUpdatable> インターフェイスを実装する利点はありません。</span><span class="sxs-lookup"><span data-stu-id="dae38-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="dae38-112">実装する例については、<xref:System.Data.Services.IUpdatable>インターフェイスを参照してください[する方法: LINQ to SQL データ ソースを使用してデータ サービスを作成](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="dae38-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="dae38-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="dae38-113">See Also</span></span>  
 [<span data-ttu-id="dae38-114">方法: SQL データ ソースを LINQ を使用してデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dae38-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [<span data-ttu-id="dae38-115">データ サービス プロバイダー</span><span class="sxs-lookup"><span data-stu-id="dae38-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="dae38-116">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dae38-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
