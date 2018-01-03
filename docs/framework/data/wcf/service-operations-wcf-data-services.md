---
title: "サービス操作 (WCF Data Services)"
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
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72af11330bc9190ea0c07e23f2e87e5f4840b677
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service-operations-wcf-data-services"></a><span data-ttu-id="40728-102">サービス操作 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="40728-102">Service Operations (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="40728-103"> では、データ サービスでサービス操作を定義して、サーバーでメソッドを公開できます。</span><span class="sxs-lookup"><span data-stu-id="40728-103"> enables you to define service operations on a data service to expose methods on the server.</span></span> <span data-ttu-id="40728-104">その他のデータ サービス リソースと同様に、サービス操作は URI によってアドレス指定できます。</span><span class="sxs-lookup"><span data-stu-id="40728-104">Like other data service resources, service operations are addressed by URIs.</span></span> <span data-ttu-id="40728-105">サービス操作では、データ サービスでビジネス ロジックを公開できます (検証ロジックの実装、ロール ベースのセキュリティの適用、特殊なクエリ機能の公開など)。</span><span class="sxs-lookup"><span data-stu-id="40728-105">Service operations enable you to expose business logic in a data service, such as to implement validation logic, to apply role-based security, or to expose specialized querying capabilities.</span></span> <span data-ttu-id="40728-106">サービス操作は、<xref:System.Data.Services.DataService%601> から派生するデータ クラスに追加されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="40728-106">Service operations are methods added to the data service class that derives from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="40728-107">その他のすべてのデータ サービス リソースと同様に、パラメーターをサービス操作メソッドに指定できます。</span><span class="sxs-lookup"><span data-stu-id="40728-107">Like all other data service resources, you can supply parameters to the service operation method.</span></span> <span data-ttu-id="40728-108">たとえば、次のサービス操作の URI (に基づいて、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)データ サービス) は、値を渡します`London`を`city`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="40728-108">For example, the following service operation URI (based on the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) data service) passes the value `London` to the `city` parameter:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 <span data-ttu-id="40728-109">このサービス操作の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40728-109">The definition for this service operation is as follows:</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 <span data-ttu-id="40728-110"><xref:System.Data.Services.DataService%601.CurrentDataSource%2A> の <xref:System.Data.Services.DataService%601> を使用して、データ サービスが使用するデータ ソースに直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="40728-110">You can use the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> of the <xref:System.Data.Services.DataService%601> to directly access the data source that the data service is using.</span></span> <span data-ttu-id="40728-111">詳細については、次を参照してください。[する方法: サービス操作を定義する](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="40728-111">For more information, see [How to: Define a Service Operation](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="40728-112">.NET Framework クライアント アプリケーションからサービス操作を呼び出す方法については、次を参照してください。[サービス操作の呼び出し](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="40728-112">For information on how to call a service operation from a .NET Framework client application, see [Calling Service Operations](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).</span></span>  
  
## <a name="service-operation-requirements"></a><span data-ttu-id="40728-113">サービス操作の要件</span><span class="sxs-lookup"><span data-stu-id="40728-113">Service Operation Requirements</span></span>  
 <span data-ttu-id="40728-114">データ サービスでサービス操作を定義する場合、次の要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="40728-114">The following requirements apply when defining service operations on the data service.</span></span> <span data-ttu-id="40728-115">これらの要件を満たしていないメソッドは、データ サービスのサービス操作として公開されません。</span><span class="sxs-lookup"><span data-stu-id="40728-115">If a method does not meet these requirements, it will not be exposed as a service operation for the data service.</span></span>  
  
-   <span data-ttu-id="40728-116">操作は、データ サービス クラスのメンバーであるパブリック インスタンス メソッドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-116">The operation must be a public instance method that is a member of the data service class.</span></span>  
  
-   <span data-ttu-id="40728-117">操作メソッドは入力パラメーターだけを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="40728-117">The operation method may only accept input parameters.</span></span> <span data-ttu-id="40728-118">メッセージの本文内で送信されるデータは、データ サービスからアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="40728-118">Data sent in the message body cannot be accessed by the data service.</span></span>  
  
-   <span data-ttu-id="40728-119">パラメーターを定義する場合、各パラメーターの型はプリミティブ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-119">If parameters are defined, the type of each parameter must be a primitive type.</span></span> <span data-ttu-id="40728-120">非プリミティブ型のいずれかのデータもシリアル化され、文字列パラメーターに渡される必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-120">Any data of a non-primitive type must be serialized and passed into a string parameter.</span></span>  
  
-   <span data-ttu-id="40728-121">メソッドは次のいずれかを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-121">The method must return one of the following:</span></span>  
  
    -   <span data-ttu-id="40728-122">`void` (Visual Basic の場合は `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="40728-122">`void` (`Nothing` in Visual Basic)</span></span>  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   <span data-ttu-id="40728-123">データ サービスが公開するデータ モデル内のエンティティ型。</span><span class="sxs-lookup"><span data-stu-id="40728-123">An entity type in the data model that the data service exposes.</span></span>  
  
    -   <span data-ttu-id="40728-124">プリミティブ クラス (整数や文字列など)。</span><span class="sxs-lookup"><span data-stu-id="40728-124">A primitive class such as integer or string.</span></span>  
  
-   <span data-ttu-id="40728-125">並べ替え、ページング、フィルター処理などのクエリ オプションをサポートするために、サービス操作メソッドから <xref:System.Linq.IQueryable%601> が返される必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-125">In order to support query options such as sorting, paging, and filtering, service operation methods should return <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="40728-126">クエリ オプションを含むサービス操作への要求は、<xref:System.Collections.Generic.IEnumerable%601> だけを返す操作で拒否されます。</span><span class="sxs-lookup"><span data-stu-id="40728-126">Requests to service operations that include query options are rejected for operations that only return <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
-   <span data-ttu-id="40728-127">ナビゲーション プロパティを使用した関連エンティティへのアクセスをサポートするために、サービス操作は <xref:System.Linq.IQueryable%601> を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-127">In order to support accessing related entities by using navigation properties, the service operation must return <xref:System.Linq.IQueryable%601>.</span></span>  
  
-   <span data-ttu-id="40728-128">メソッドには、`[WebGet]` 属性または `[WebInvoke]` 属性を使用して注釈を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-128">The method must be annotated with the `[WebGet]` or `[WebInvoke]` attribute.</span></span>  
  
    -   <span data-ttu-id="40728-129">`[WebGet]` では、GET 要求を使用してメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="40728-129">`[WebGet]` enables the method to be invoked by using a GET request.</span></span>  
  
    -   <span data-ttu-id="40728-130">`[WebInvoke(Method = "POST")]` では、POST 要求を使用してメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="40728-130">`[WebInvoke(Method = "POST")]` enables the method to be invoked by using a POST request.</span></span> <span data-ttu-id="40728-131">その他の <xref:System.ServiceModel.Web.WebInvokeAttribute> メソッドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="40728-131">Other <xref:System.ServiceModel.Web.WebInvokeAttribute> methods are not supported.</span></span>  
  
-   <span data-ttu-id="40728-132">サービス操作には、<xref:System.Data.Services.SingleResultAttribute> を使用して注釈を付けることができます。この属性は、メソッドからの戻り値がエンティティのコレクションではなく 1 つのエンティティとなるように指定します。</span><span class="sxs-lookup"><span data-stu-id="40728-132">A service operation may be annotated with the <xref:System.Data.Services.SingleResultAttribute> that specifies that the return value from the method is a single entity rather than a collection of entities.</span></span> <span data-ttu-id="40728-133">この区別により、応答の結果のシリアル化、および追加のナビゲーション プロパティのトラバーサルを URI で表す方法が決定されます。</span><span class="sxs-lookup"><span data-stu-id="40728-133">This distinction dictates the resulting serialization of the response and the manner in which additional navigation property traversals are represented in the URI.</span></span> <span data-ttu-id="40728-134">たとえば、AtomPub シリアル化を使用すると、1 種類のリソースのインスタンスがエントリ要素として表され、一連のインスタンスがフィード要素として表されます。</span><span class="sxs-lookup"><span data-stu-id="40728-134">For example, when using AtomPub serialization, a single resource type instance is represented as an entry element and a set of instances as a feed element.</span></span>  
  
## <a name="addressing-service-operations"></a><span data-ttu-id="40728-135">サービス操作のアドレス指定</span><span class="sxs-lookup"><span data-stu-id="40728-135">Addressing Service Operations</span></span>  
 <span data-ttu-id="40728-136">メソッドの名前を URI の最初のパス セグメントに配置することによってサービス操作のアドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="40728-136">You can address service operations by placing the name of the method in the first path segment of a URI.</span></span> <span data-ttu-id="40728-137">たとえば、次の URI の場合、`GetOrdersByState` オブジェクトの <xref:System.Linq.IQueryable%601> コレクションを返す `Orders` 操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="40728-137">As an example, the following URI accesses a `GetOrdersByState` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects.</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 <span data-ttu-id="40728-138">サービス操作を呼び出すときは、パラメーターはクエリのオプションとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="40728-138">When calling a service operation, parameters are supplied as query options.</span></span> <span data-ttu-id="40728-139">前のサービス操作は、文字列パラメーター `state` と、関連する `includeItems` オブジェクトを応答に含めるかどうかを指定するブール値パラメーター `Order_Detail` の両方を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="40728-139">The previous service operation accepts both a string parameter `state` and a Boolean parameter `includeItems` that indicates whether to include related `Order_Detail` objects in the response.</span></span>  
  
 <span data-ttu-id="40728-140">サービス操作の有効な戻り値の型を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40728-140">The following are valid return types for a service operation:</span></span>  
  
|<span data-ttu-id="40728-141">有効な戻り値の型</span><span class="sxs-lookup"><span data-stu-id="40728-141">Valid Return Types</span></span>|<span data-ttu-id="40728-142">URI のルール</span><span class="sxs-lookup"><span data-stu-id="40728-142">URI Rules</span></span>|  
|------------------------|---------------|  
|<span data-ttu-id="40728-143">`void` (Visual Basic の場合は `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="40728-143">`void` (`Nothing` in Visual Basic)</span></span><br /><br /> <span data-ttu-id="40728-144">または</span><span class="sxs-lookup"><span data-stu-id="40728-144">-or-</span></span><br /><br /> <span data-ttu-id="40728-145">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="40728-145">Entity types</span></span><br /><br /> <span data-ttu-id="40728-146">または</span><span class="sxs-lookup"><span data-stu-id="40728-146">-or-</span></span><br /><br /> <span data-ttu-id="40728-147">プリミティブ型</span><span class="sxs-lookup"><span data-stu-id="40728-147">Primitive types</span></span>|<span data-ttu-id="40728-148">URI は、サービス操作の名前である 1 つのパス セグメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-148">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="40728-149">クエリ オプションは許可されません。</span><span class="sxs-lookup"><span data-stu-id="40728-149">Query options are not allowed.</span></span>|  
|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="40728-150">URI は、サービス操作の名前である 1 つのパス セグメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="40728-150">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="40728-151">結果型は <xref:System.Linq.IQueryable%601> 型ではないので、クエリ オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="40728-151">Because the result type is not an <xref:System.Linq.IQueryable%601> type, query options are not allowed.</span></span>|  
|<xref:System.Linq.IQueryable%601>|<span data-ttu-id="40728-152">サービス操作の名前であるパスに追加したクエリ パス セグメント セグメントが許可されます。</span><span class="sxs-lookup"><span data-stu-id="40728-152">Query path segments in addition to the path that is the name of the service operation are allowed.</span></span> <span data-ttu-id="40728-153">クエリ オプションも許可されます。</span><span class="sxs-lookup"><span data-stu-id="40728-153">Query options are also allowed.</span></span>|  
  
 <span data-ttu-id="40728-154">サービス操作の戻り値の型によっては、パス セグメントやクエリ オプションをさらに URI に追加できます。</span><span class="sxs-lookup"><span data-stu-id="40728-154">Additional path segments or query options may be added to the URI depending on the return type of the service operation.</span></span> <span data-ttu-id="40728-155">たとえば、次の URI は、関連する `GetOrdersByCity` オブジェクトと一緒に <xref:System.Linq.IQueryable%601> オブジェクトの `Orders` コレクションを `RequiredDate` の降順で返す `Order_Details` 操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="40728-155">For example, the following URI accesses a `GetOrdersByCity` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects, ordered by `RequiredDate` in descending order, along with the related `Order_Details` objects:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a><span data-ttu-id="40728-156">サービス操作のアクセス制御</span><span class="sxs-lookup"><span data-stu-id="40728-156">Service Operations Access Control</span></span>  
 <span data-ttu-id="40728-157">サービス操作のサービス全体の表示は、エンティティ セットの表示が <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> メソッドを使用して制御されるのと同じような方法で、<xref:System.Data.Services.IDataServiceConfiguration> クラスの <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> メソッドによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="40728-157">Service-wide visibility of service operations is controlled by the <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> method on the <xref:System.Data.Services.IDataServiceConfiguration> class in much the same way that entity set visibility is controlled by using the <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> method.</span></span> <span data-ttu-id="40728-158">たとえば、データ サービス定義内の次のコード行は、`CustomersByCity` サービス操作へのアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="40728-158">For example, the following line of code in the data service definition enables access to the `CustomersByCity` service operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  <span data-ttu-id="40728-159">元になるエンティティ セットの制限アクセスによって非表示にされている戻り値の型がサービス操作にある場合、サービス操作はクライアント アプリケーションで使用できません。</span><span class="sxs-lookup"><span data-stu-id="40728-159">If a service operation has a return type that has been hidden by restricting access on the underlying entity sets, then the service operation will not be available to client applications.</span></span>  
  
 <span data-ttu-id="40728-160">詳細については、次を参照してください。[する方法: サービス操作を定義する](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="40728-160">For more information, see [How to: Define a Service Operation](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span></span>  
  
## <a name="raising-exceptions"></a><span data-ttu-id="40728-161">例外の発生</span><span class="sxs-lookup"><span data-stu-id="40728-161">Raising Exceptions</span></span>  
 <span data-ttu-id="40728-162">データ サービスの実行で例外が発生するたびに、<xref:System.Data.Services.DataServiceException> クラスを使用することお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40728-162">We recommend that you use the <xref:System.Data.Services.DataServiceException> class whenever you raise an exception in the data service execution.</span></span> <span data-ttu-id="40728-163">これは、データ サービス ランタイムがこの例外のオブジェクトのプロパティを HTTP 応答メッセージに正しくマップする方法を認識しているためです。</span><span class="sxs-lookup"><span data-stu-id="40728-163">This is because the data service runtime knows how to map properties of this exception object correctly to the HTTP response message.</span></span> <span data-ttu-id="40728-164">サービス操作で <xref:System.Data.Services.DataServiceException> が発生する場合、返された例外は <xref:System.Reflection.TargetInvocationException> にラップされています。</span><span class="sxs-lookup"><span data-stu-id="40728-164">When you raise a <xref:System.Data.Services.DataServiceException> in a service operation, the returned exception is wrapped in a <xref:System.Reflection.TargetInvocationException>.</span></span> <span data-ttu-id="40728-165"><xref:System.Data.Services.DataServiceException> をラップせずにベース <xref:System.Reflection.TargetInvocationException> を返すには、<xref:System.Data.Services.DataService%601.HandleException%2A> の <xref:System.Data.Services.DataService%601> メソッドをオーバーライドし、<xref:System.Data.Services.DataServiceException> から <xref:System.Reflection.TargetInvocationException> を抽出して、トップ レベル エラーとして返す必要があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="40728-165">To return the base <xref:System.Data.Services.DataServiceException> without the enclosing <xref:System.Reflection.TargetInvocationException>, you must override the <xref:System.Data.Services.DataService%601.HandleException%2A> method in the <xref:System.Data.Services.DataService%601>, extract the <xref:System.Data.Services.DataServiceException> from the <xref:System.Reflection.TargetInvocationException>, and return it as the top-level error, as in the following example:</span></span>  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a><span data-ttu-id="40728-166">参照</span><span class="sxs-lookup"><span data-stu-id="40728-166">See Also</span></span>  
 [<span data-ttu-id="40728-167">インターセプター</span><span class="sxs-lookup"><span data-stu-id="40728-167">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
