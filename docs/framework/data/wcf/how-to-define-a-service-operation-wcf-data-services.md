---
title: "方法: サービス操作を定義する (WCF Data Services)"
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
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcf4ffd46bbbca0e7e00cad7ae0b2a88f7bd986b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="b6192-102">方法: サービス操作を定義する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="b6192-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="b6192-103"> は、サーバー上でサービス操作として定義されたメソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="b6192-103"> expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="b6192-104">サービス操作では、サーバーで定義されているメソッドに URI を介してアクセスを提供するデータ サービスを許可します。</span><span class="sxs-lookup"><span data-stu-id="b6192-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="b6192-105">サービス操作を定義するのには、適用、[`WebGet]`または`[WebInvoke]`属性をメソッドにします。</span><span class="sxs-lookup"><span data-stu-id="b6192-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="b6192-106">クエリ演算子をサポートするために、サービス操作が返す必要があります、<xref:System.Linq.IQueryable%601>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="b6192-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="b6192-107">サービス操作は、<xref:System.Data.Services.DataService%601.CurrentDataSource%2A> の <xref:System.Data.Services.DataService%601> プロパティを介して、基になるデータ ソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b6192-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="b6192-108">詳細については、次を参照してください。[サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6192-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="b6192-109">このトピックの例では、`GetOrdersByCity` という名前のサービス操作を定義します。このサービス操作は、<xref:System.Linq.IQueryable%601> オブジェクトおよび関連する `Orders` オブジェクトのフィルターされた `Order_Details` インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="b6192-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="b6192-110">この例は、Northwind サンプル データ サービスのデータ ソースである <xref:System.Data.Objects.ObjectContext> インスタンスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b6192-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="b6192-111">このサービスの作成が完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6192-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="b6192-112">Northwind データ サービスのサービス操作を定義するには</span><span class="sxs-lookup"><span data-stu-id="b6192-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="b6192-113">Northwind データ サービス プロジェクトで Northwind.svc ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6192-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="b6192-114">`Northwind` クラスで、次に示すように `GetOrdersByCity` というサービス操作メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6192-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="b6192-115">`InitializeService` クラスの `Northwind` メソッドで次のコードを追加して、サービス操作へのアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b6192-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="b6192-116">GetOrdersByCity サービス操作をクエリするには</span><span class="sxs-lookup"><span data-stu-id="b6192-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="b6192-117">Web ブラウザーで次のいずれかの URI を入力して、次の例で定義されているサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b6192-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="b6192-118">例</span><span class="sxs-lookup"><span data-stu-id="b6192-118">Example</span></span>  
 <span data-ttu-id="b6192-119">次の例は、`GetOrderByCity` という名前のサービス操作を Northwind データ サービスに実装します。</span><span class="sxs-lookup"><span data-stu-id="b6192-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="b6192-120">この操作は、ADO.NET Entity Framework を使用して、`Orders` オブジェクトのセットおよび関連する `Order_Details` オブジェクトを、指定した都市名に基づく <xref:System.Linq.IQueryable%601> インスタンスとして返します。</span><span class="sxs-lookup"><span data-stu-id="b6192-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6192-121">メソッドは <xref:System.Linq.IQueryable%601> インスタンスを返すので、クエリ操作は、このサービス操作エンドポイントでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b6192-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="b6192-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6192-122">See Also</span></span>  
 [<span data-ttu-id="b6192-123">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="b6192-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
