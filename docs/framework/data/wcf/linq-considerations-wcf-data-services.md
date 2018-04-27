---
title: LINQ に関する留意点 (WCF Data Services)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df596093333aa35b89f8d7ed36f817a457e48fda
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="linq-considerations-wcf-data-services"></a><span data-ttu-id="690ec-102">LINQ に関する留意点 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="690ec-102">LINQ Considerations (WCF Data Services)</span></span>
<span data-ttu-id="690ec-103">このトピックでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントを使用しているときに LINQ クエリを作成および実行する方法と、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を実装するデータ サービスを LINQ で照会する場合の制限について説明します。</span><span class="sxs-lookup"><span data-stu-id="690ec-103">This topic provides information about the way in which LINQ queries are composed and executed when you are using the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client and limitations of using LINQ to query a data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)].</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="690ec-104"> 作成し、に対するクエリの実行、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのデータ サービスを参照してください[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="690ec-104"> composing and executing queries against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based data service, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="composing-linq-queries"></a><span data-ttu-id="690ec-105">LINQ クエリの作成</span><span class="sxs-lookup"><span data-stu-id="690ec-105">Composing LINQ Queries</span></span>  
 <span data-ttu-id="690ec-106">LINQ を使用すると、<xref:System.Collections.Generic.IEnumerable%601> を実装するオブジェクトのコレクションに対するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="690ec-106">LINQ enables you to compose queries against a collection of objects that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="690ec-107">両方の**サービス参照の追加**Visual Studio のダイアログ ボックスと DataSvcUtil.exe ツールは、の形式の生成に使用される、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]サービスから継承するエンティティ コンテナー クラスとして<xref:System.Data.Services.Client.DataServiceContext>、だけでなくフィードで返されるエンティティを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="690ec-107">Both the **Add Service Reference** dialog box in Visual Studio and the DataSvcUtil.exe tool are used to generate a representation of an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>, as well as objects that represent the entities returned in feeds.</span></span> <span data-ttu-id="690ec-108">これらのツールでは、サービスによってフィードとして公開されるコレクションに対応するエンティティ コンテナー クラスのプロパティも生成されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-108">These tools also generate properties on the entity container class for the collections that are exposed as feeds by the service.</span></span> <span data-ttu-id="690ec-109">データ サービスをカプセル化するクラスのこれらのプロパティは、それぞれ <xref:System.Data.Services.Client.DataServiceQuery%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="690ec-109">Each of these properties of the class that encapsulates the data service return a <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span> <span data-ttu-id="690ec-110"><xref:System.Data.Services.Client.DataServiceQuery%601> クラスは LINQ で定義された <xref:System.Linq.IQueryable%601> インターフェイスを実装するので、データ サービスによって公開されるフィードに対する LINQ クエリを作成できます。作成した LINQ クエリは、クライアント ライブラリにより、実行時にデータ サービスに送信されるクエリ要求 URI に変換されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-110">Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, you can compose a LINQ query against feeds exposed by the data service, which are translated by the client library into a query request URI that is sent to the data service on execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="690ec-111">LINQ 構文で表現できるクエリのセットは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] データ サービスによって使用される URI 構文で有効なクエリのセットよりも範囲が広くなります。</span><span class="sxs-lookup"><span data-stu-id="690ec-111">The set of queries expressible in the LINQ syntax is broader than those enabled in the URI syntax that is used by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data services.</span></span> <span data-ttu-id="690ec-112">クエリを対象データ サービスの URI にマップできない場合、<xref:System.NotSupportedException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="690ec-112">A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="690ec-113"> [サポートされていない LINQ メソッド](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods)」を参照します。</span><span class="sxs-lookup"><span data-stu-id="690ec-113"> the [Unsupported LINQ Methods](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) in this topic.</span></span>  
  
 <span data-ttu-id="690ec-114">次の例の LINQ クエリは、輸送費が 30 ドルを超える `Orders` を取得し、結果を出荷日の新しい順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="690ec-114">The following example is a LINQ query that returns `Orders` that have a freight cost of more than $30 and sorts the results by the shipping date, starting with the latest ship date:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 <span data-ttu-id="690ec-115">この LINQ クエリは次のクエリ、Northwind ベースに対して実行される URI に変換[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)データ サービス。</span><span class="sxs-lookup"><span data-stu-id="690ec-115">This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) data service:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 <span data-ttu-id="690ec-116">LINQ の概要については、次を参照してください。[クエリ (LINQ: Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)です。</span><span class="sxs-lookup"><span data-stu-id="690ec-116">For more general information about LINQ, see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>  
  
 <span data-ttu-id="690ec-117">LINQ を使用してクエリを作成する際には、前の例のような言語固有の宣言型のクエリ構文と、標準クエリ演算子と呼ばれる一連のクエリ メソッドの両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="690ec-117">LINQ enables you to compose queries by using both the language-specific declarative query syntax, shown in the previous example, as well as a set of query methods known as standard query operators.</span></span> <span data-ttu-id="690ec-118">したがって、次の例のように、前の例と同等のクエリをメソッド ベースの構文のみを使用して作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="690ec-118">An equivalent query to the previous example can be composed by using only the method-based syntax, as shown the following example:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 <span data-ttu-id="690ec-119">どちらの方法で作成したクエリも、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントによってクエリ URI に変換されます。クエリ式にクエリ メソッドを追加して LINQ クエリを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="690ec-119">The [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client is able to translate both kinds of composed queries into a query URI, and you can extend a LINQ query by appending query methods to a query expression.</span></span> <span data-ttu-id="690ec-120">クエリ式または <xref:System.Data.Services.Client.DataServiceQuery%601> にメソッド構文を追加して LINQ クエリを作成した場合は、メソッドが呼び出される順序で操作がクエリ URI に追加されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-120">When you compose LINQ queries by appending method syntax to a query expression or a <xref:System.Data.Services.Client.DataServiceQuery%601>, the operations are added to the query URI in the order in which methods are called.</span></span> <span data-ttu-id="690ec-121">これは、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを呼び出して各クエリ オプションをクエリ URI に追加するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="690ec-121">This is equivalent to calling the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to add each query option to the query URI.</span></span>  
  
## <a name="executing-linq-queries"></a><span data-ttu-id="690ec-122">LINQ クエリの実行</span><span class="sxs-lookup"><span data-stu-id="690ec-122">Executing LINQ Queries</span></span>  
 <span data-ttu-id="690ec-123">クエリに特定の LINQ クエリ メソッド (<xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>、<xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> など) を追加するとクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-123">Certain LINQ query methods, such as <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> or <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, when appended to the query, cause the query to be executed.</span></span> <span data-ttu-id="690ec-124">クエリは、結果が暗黙的に列挙される場合 (`foreach` ループの間など) や、クエリが `List` コレクションに割り当てられている場合にも実行されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-124">A query is also executed when results are enumerated implicitly, such as during a `foreach` loop or when the query is assigned to a `List` collection.</span></span> <span data-ttu-id="690ec-125">詳細については、次を参照してください。[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="690ec-125">For more information, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="690ec-126">クライアントによる LINQ クエリの実行は 2 つの部分に分かれています。</span><span class="sxs-lookup"><span data-stu-id="690ec-126">The client executes a LINQ query in two parts.</span></span> <span data-ttu-id="690ec-127">可能な限り、クエリ内の LINQ 式は最初にクライアントで評価されます。その後、URI ベースのクエリが生成され、データ サービスに送信されて、サービス内のデータに対して評価されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-127">Whenever possible, LINQ expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service.</span></span> <span data-ttu-id="690ec-128">詳細については、セクションを参照して[サーバーの実行とクライアント](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries)で[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="690ec-128">For more information, see the section [Client versus Server Execution](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) in [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="690ec-129">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 準拠のクエリ URI で LINQ クエリを変換できない場合は、クエリを実行しようとすると例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="690ec-129">When a LINQ query cannot be translated in an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-compliant query URI, an exception is raised when execution is attempted.</span></span> <span data-ttu-id="690ec-130">詳細については、次を参照してください。[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="690ec-130">For more information, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="linq-query-examples"></a><span data-ttu-id="690ec-131">LINQ クエリの例</span><span class="sxs-lookup"><span data-stu-id="690ec-131">LINQ Query Examples</span></span>  
 <span data-ttu-id="690ec-132">以下のセクションの各例は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに対して実行できる LINQ クエリの種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="690ec-132">The examples in the following sections demonstrate the kinds of LINQ queries that can be executed against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service.</span></span>  
  
<a name="filtering"></a>   
### <a name="filtering"></a><span data-ttu-id="690ec-133">フィルター処理</span><span class="sxs-lookup"><span data-stu-id="690ec-133">Filtering</span></span>  
 <span data-ttu-id="690ec-134">このセクションの LINQ クエリは、サービスによって返されるフィード内のデータをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="690ec-134">The LINQ query examples in this section filter data in the feed returned by the service.</span></span>  
  
 <span data-ttu-id="690ec-135">以下の各例は、返された `Orders` エンティティをフィルター処理して、輸送費が 30 ドルを超える注文のみが返されるようにする同等のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="690ec-135">The following examples are equivalent queries that filter the returned `Orders` entities so that only orders with a freight cost greater than $30 are returned:</span></span>  
  
-   <span data-ttu-id="690ec-136">LINQ クエリ構文を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-136">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   <span data-ttu-id="690ec-137">LINQ クエリ メソッドを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-137">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   <span data-ttu-id="690ec-138">URI クエリ文字列オプション `$filter`:</span><span class="sxs-lookup"><span data-stu-id="690ec-138">The URI query string `$filter` option:</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 <span data-ttu-id="690ec-139">上の例はすべて、`http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M` というクエリ URI に変換されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-139">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span></span>  
  
<a name="sorting"></a>   
### <a name="sorting"></a><span data-ttu-id="690ec-140">並べ替え</span><span class="sxs-lookup"><span data-stu-id="690ec-140">Sorting</span></span>  
 <span data-ttu-id="690ec-141">以下の各例は、返されたデータを会社名と郵便番号の降順で並べ替える同等のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="690ec-141">The following examples show equivalent queries that sort returned data both by the company name and by postal code, descending:</span></span>  
  
-   <span data-ttu-id="690ec-142">LINQ クエリ構文を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-142">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   <span data-ttu-id="690ec-143">LINQ クエリ メソッドを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-143">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   <span data-ttu-id="690ec-144">URI クエリ文字列オプション `$orderby`:</span><span class="sxs-lookup"><span data-stu-id="690ec-144">URI query string `$orderby` option):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 <span data-ttu-id="690ec-145">上の例はすべて、`http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc` というクエリ URI に変換されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-145">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span></span>  
  
<a name="projection"></a>   
### <a name="projection"></a><span data-ttu-id="690ec-146">射影</span><span class="sxs-lookup"><span data-stu-id="690ec-146">Projection</span></span>  
 <span data-ttu-id="690ec-147">以下の各例は、返されたデータをより範囲の狭い `CustomerAddress` 型に射影する同等のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="690ec-147">The following examples show equivalent queries that project returned data into the narrower `CustomerAddress` type:</span></span>  
  
-   <span data-ttu-id="690ec-148">LINQ クエリ構文を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-148">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   <span data-ttu-id="690ec-149">LINQ クエリ メソッドを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-149">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  <span data-ttu-id="690ec-150">`$select` メソッドを使用してクエリ URI に <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> クエリ オプションを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="690ec-150">The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="690ec-151">LINQ の <xref:System.Linq.Enumerable.Select%2A> メソッドを使用して、クライアントによって要求 URI に `$select` クエリ オプションが生成されるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="690ec-151">We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.</span></span>  
  
 <span data-ttu-id="690ec-152">上の例はいずれも、`"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"` というクエリ URI に変換されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-152">Both of the previous examples are translated to the query URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span></span>  
  
<a name="paging"></a>   
### <a name="client-paging"></a><span data-ttu-id="690ec-153">クライアントのページング</span><span class="sxs-lookup"><span data-stu-id="690ec-153">Client Paging</span></span>  
 <span data-ttu-id="690ec-154">以下の各例は、25 件の注文を含む並べ替え済みの注文エンティティのページを、最初の 50 件の注文をスキップして要求する同等のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="690ec-154">The following examples show equivalent queries that request a page of sorted order entities that includes 25 orders, skipping the first 50 orders:</span></span>  
  
-   <span data-ttu-id="690ec-155">LINQ クエリにクエリ メソッドを適用する場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-155">Applying query methods to a LINQ query:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   <span data-ttu-id="690ec-156">URI クエリ文字列オプション `$skip` および `$top`:</span><span class="sxs-lookup"><span data-stu-id="690ec-156">URI query string `$skip` and `$top` options):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 <span data-ttu-id="690ec-157">上の例はいずれも、`http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25` というクエリ URI に変換されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-157">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span></span>  
  
<a name="expand"></a>   
### <a name="expand"></a><span data-ttu-id="690ec-158">Expand</span><span class="sxs-lookup"><span data-stu-id="690ec-158">Expand</span></span>  
 <span data-ttu-id="690ec-159">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] データ サービスを照会するときに、返されるフィードにクエリの対象のエンティティに関連するエンティティを含めるように要求することができます。</span><span class="sxs-lookup"><span data-stu-id="690ec-159">When you query an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data service, you can request that entities related to the entity targeted by the query be included the returned feed.</span></span> <span data-ttu-id="690ec-160">そのためには、LINQ クエリの対象のエンティティ セットの <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> で <xref:System.Data.Services.Client.DataServiceQuery%601> メソッドを呼び出して、関連するエンティティ セットの名前を `path` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="690ec-160">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is called on the <xref:System.Data.Services.Client.DataServiceQuery%601> for the entity set targeted by the LINQ query, with the related entity set name supplied as the `path` parameter.</span></span> <span data-ttu-id="690ec-161">詳細については、次を参照してください。[遅延コンテンツを読み込んで](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="690ec-161">For more information, see [Loading Deferred Content](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="690ec-162">以下の各例は、クエリで <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用する同等の方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="690ec-162">The following examples show equivalent ways to use the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method in a query:</span></span>  
  
-   <span data-ttu-id="690ec-163">LINQ クエリ構文の場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-163">In LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   <span data-ttu-id="690ec-164">LINQ クエリ メソッドの場合:</span><span class="sxs-lookup"><span data-stu-id="690ec-164">With LINQ query methods:</span></span>  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 <span data-ttu-id="690ec-165">上の例はいずれも、`http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details` というクエリ URI に変換されます。</span><span class="sxs-lookup"><span data-stu-id="690ec-165">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span></span>  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a><span data-ttu-id="690ec-166">サポートされていない LINQ メソッド</span><span class="sxs-lookup"><span data-stu-id="690ec-166">Unsupported LINQ Methods</span></span>  
 <span data-ttu-id="690ec-167">次の表に含まれている LINQ メソッドはサポートされていません。[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに対して実行されるクエリにこれらのメソッドを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="690ec-167">The following table contains the classes of LINQ methods are not supported and cannot be included in a query executed against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service:</span></span>  
  
|<span data-ttu-id="690ec-168">演算の種類</span><span class="sxs-lookup"><span data-stu-id="690ec-168">Operation Type</span></span>|<span data-ttu-id="690ec-169">サポートされていないメソッド</span><span class="sxs-lookup"><span data-stu-id="690ec-169">Unsupported Method</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="690ec-170">集合演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-170">Set operators</span></span>|<span data-ttu-id="690ec-171">すべての集合演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="690ec-171">All set operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, which included the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|<span data-ttu-id="690ec-172">順序付け演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-172">Ordering operators</span></span>|<span data-ttu-id="690ec-173"><xref:System.Collections.Generic.IComparer%601> を必要とする以下の順序付け演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="690ec-173">The following ordering operators that require <xref:System.Collections.Generic.IComparer%601> are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|<span data-ttu-id="690ec-174">プロジェクション演算子とフィルター演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-174">Projection and filtering operators</span></span>|<span data-ttu-id="690ec-175">位置指定引数を受け取る以下のプロジェクション演算子とフィルター演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="690ec-175">The following projection and filtering operators that accept a positional argument are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|<span data-ttu-id="690ec-176">グループ化演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-176">Grouping operators</span></span>|<span data-ttu-id="690ec-177">すべてのグループ化演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="690ec-177">All grouping operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> <span data-ttu-id="690ec-178">グループ化の操作はクライアント側で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="690ec-178">Grouping operations must be performed on the client.</span></span>|  
|<span data-ttu-id="690ec-179">集計演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-179">Aggregate operators</span></span>|<span data-ttu-id="690ec-180">すべての集計演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="690ec-180">All aggregate operations are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> <span data-ttu-id="690ec-181">集計操作は、クライアント側で実行するか、サービス操作でカプセル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="690ec-181">Aggregate operations must either be performed on the client or be encapsulated by a service operation.</span></span>|  
|<span data-ttu-id="690ec-182">ページング演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-182">Paging operators</span></span>|<span data-ttu-id="690ec-183">以下のページング演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="690ec-183">The following paging operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br /><span data-ttu-id="690ec-184">-   <xref:System.Linq.Enumerable.TakeWhile%2A> **注:** null、空のシーケンスで実行されるページング演算子を返します。</span><span class="sxs-lookup"><span data-stu-id="690ec-184">-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Note:**  Paging operators that are executed on an empty sequence return null.</span></span>|  
|<span data-ttu-id="690ec-185">その他の演算子</span><span class="sxs-lookup"><span data-stu-id="690ec-185">Other operators</span></span>|<span data-ttu-id="690ec-186">以下に示す演算子は <xref:System.Data.Services.Client.DataServiceQuery%601> に対してサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="690ec-186">The following other operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> <span data-ttu-id="690ec-187">1.  <xref:System.Linq.Enumerable.Empty%2A></span><span class="sxs-lookup"><span data-stu-id="690ec-187">1.  <xref:System.Linq.Enumerable.Empty%2A></span></span><br /><span data-ttu-id="690ec-188">2.  <xref:System.Linq.Enumerable.Range%2A></span><span class="sxs-lookup"><span data-stu-id="690ec-188">2.  <xref:System.Linq.Enumerable.Range%2A></span></span><br /><span data-ttu-id="690ec-189">3.  <xref:System.Linq.Enumerable.Repeat%2A></span><span class="sxs-lookup"><span data-stu-id="690ec-189">3.  <xref:System.Linq.Enumerable.Repeat%2A></span></span><br /><span data-ttu-id="690ec-190">4.  <xref:System.Linq.Enumerable.ToDictionary%2A></span><span class="sxs-lookup"><span data-stu-id="690ec-190">4.  <xref:System.Linq.Enumerable.ToDictionary%2A></span></span><br /><span data-ttu-id="690ec-191">5.  <xref:System.Linq.Enumerable.ToLookup%2A></span><span class="sxs-lookup"><span data-stu-id="690ec-191">5.  <xref:System.Linq.Enumerable.ToLookup%2A></span></span>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a><span data-ttu-id="690ec-192">サポートされている式の関数</span><span class="sxs-lookup"><span data-stu-id="690ec-192">Supported Expression Functions</span></span>  
 <span data-ttu-id="690ec-193">共通言語ランタイム (CLR) の以下のメソッドおよびプロパティは、クエリ式で変換して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスへの要求 URI に含めることができるため、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="690ec-193">The following common-language runtime (CLR) methods and properties are supported because they can be translated in a query expression for inclusion in the request URI to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service:</span></span>  
  
|<span data-ttu-id="690ec-194"><xref:System.String> メンバー</span><span class="sxs-lookup"><span data-stu-id="690ec-194"><xref:System.String> Member</span></span>|<span data-ttu-id="690ec-195">サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数</span><span class="sxs-lookup"><span data-stu-id="690ec-195">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<span data-ttu-id="690ec-196"><xref:System.DateTime> メンバー<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="690ec-196"><xref:System.DateTime> Member<sup>1</sup></span></span>|<span data-ttu-id="690ec-197">サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数</span><span class="sxs-lookup"><span data-stu-id="690ec-197">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <span data-ttu-id="690ec-198"><sup>1</sup>、等価の日付と時刻のプロパティの<xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>、だけでなく<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>Visual Basic のメソッドもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="690ec-198"><sup>1</sup>The equivalent date and time properties of <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, as well as the <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> method in Visual Basic are also supported.</span></span>  
  
|<span data-ttu-id="690ec-199"><xref:System.Math> メンバー</span><span class="sxs-lookup"><span data-stu-id="690ec-199"><xref:System.Math> Member</span></span>|<span data-ttu-id="690ec-200">サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数</span><span class="sxs-lookup"><span data-stu-id="690ec-200">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<span data-ttu-id="690ec-201"><xref:System.Linq.Expressions.Expression> メンバー</span><span class="sxs-lookup"><span data-stu-id="690ec-201"><xref:System.Linq.Expressions.Expression> Member</span></span>|<span data-ttu-id="690ec-202">サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数</span><span class="sxs-lookup"><span data-stu-id="690ec-202">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 <span data-ttu-id="690ec-203">クライアント側でその他の CLR 関数を評価できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="690ec-203">The client may also be able to evaluate additional CLR functions on the client.</span></span> <span data-ttu-id="690ec-204">クライアント側で評価することも、サーバー側で評価するために有効な要求 URI に変換することもできない式に対しては、<xref:System.NotSupportedException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="690ec-204">A <xref:System.NotSupportedException> is raised for any expression that cannot be evaluated on the client and cannot be translated into a valid request URI for evaluation on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690ec-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="690ec-205">See Also</span></span>  
 [<span data-ttu-id="690ec-206">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="690ec-206">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [<span data-ttu-id="690ec-207">クエリ射影</span><span class="sxs-lookup"><span data-stu-id="690ec-207">Query Projections</span></span>](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [<span data-ttu-id="690ec-208">オブジェクトの具体化</span><span class="sxs-lookup"><span data-stu-id="690ec-208">Object Materialization</span></span>](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [<span data-ttu-id="690ec-209">OData: URI 規則</span><span class="sxs-lookup"><span data-stu-id="690ec-209">OData: URI Conventions</span></span>](http://go.microsoft.com/fwlink/?LinkID=185564)
