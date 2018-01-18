---
title: "N 層アプリケーションでのデータ取得および CUD 操作 (LINQ to SQL)"
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
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6cdf1a859595c82b8eea60311c3c96353849e3dc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="53636-102">N 層アプリケーションでのデータ取得および CUD 操作 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="53636-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="53636-103">Customers または Orders のようなエンティティ オブジェクトをネットワークを介してクライアントにシリアル化すると、これらのエンティティはデータ コンテキストからデタッチされます。</span><span class="sxs-lookup"><span data-stu-id="53636-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="53636-104">変更内容、および他のオブジェクトとの関連付けはデータ コンテキストによって追跡されなくなります。</span><span class="sxs-lookup"><span data-stu-id="53636-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="53636-105">クライアントがデータを読み取るだけの場合は、これは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="53636-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="53636-106">また、クライアントが新しい行をデータベースに追加できるようにすることも、ある程度簡単です。</span><span class="sxs-lookup"><span data-stu-id="53636-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="53636-107">しかし、アプリケーションでクライアントによるデータの更新または削除を可能にする必要がある場合には、<xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType> を呼び出す前に、新しいデータ コンテキストにエンティティをアタッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="53636-108">さらに、元の値によるオプティミスティック同時実行制御チェックを使用する場合には、何らかの方法で、元のエンティティと変更後のエンティティをデータベースに渡す必要もあります。</span><span class="sxs-lookup"><span data-stu-id="53636-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="53636-109">エンティティがデタッチされた後に新しいデータ コンテキストにエンティティを入れるために、`Attach` メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="53636-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="53636-110">代わりにプロキシ オブジェクトをシリアル化する場合でも、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 、エンティティがあるデータ アクセス層 (DAL) 上のエンティティを作成して、新しいアタッチ<xref:System.Data.Linq.DataContext?displayProperty=nameWithType>データベースにデータを送信するためにします。</span><span class="sxs-lookup"><span data-stu-id="53636-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="53636-111">エンティティをシリアル化する方法について完全に無関心です。</span><span class="sxs-lookup"><span data-stu-id="53636-111"> is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="53636-112">使用する方法についての詳細、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]し、Windows Communication Foundation (WCF) を使用してシリアル化できるクラスを生成する SQLMetal ツールを参照してください[する方法: エンティティをシリアル化](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-112">For more information about how to use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53636-113">`Attach` メソッドは、新しいエンティティまたは逆シリアル化されたエンティティに対してのみ呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="53636-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="53636-114">エンティティを元のデータ コンテキストからデタッチする唯一の方法は、シリアル化です。</span><span class="sxs-lookup"><span data-stu-id="53636-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="53636-115">デタッチされていないエンティティを新しいデータ コンテキストにアタッチしようとした場合、元のデータ コンテキストの遅延ローダーがそのエンティティにまだ存在するならば、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="53636-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="53636-116">2 つの異なるデータ コンテキストの遅延ローダーを持つエンティティに対して、挿入、更新、および削除操作を実行すると、予想外の結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="53636-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="53636-117">遅延ローダーの詳細については、次を参照してください。[遅延実行と即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="53636-118">データの取得</span><span class="sxs-lookup"><span data-stu-id="53636-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="53636-119">クライアントのメソッド呼び出し</span><span class="sxs-lookup"><span data-stu-id="53636-119">Client Method Call</span></span>  
 <span data-ttu-id="53636-120">Windows フォーム クライアントから DAL に対するメソッド呼び出しの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="53636-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="53636-121">この例では、DAL は Windows サービス ライブラリとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="53636-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =   
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =   
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,   
    // the client needs to store them and pass them back to the   
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="53636-122">中間層での実装</span><span class="sxs-lookup"><span data-stu-id="53636-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="53636-123">次の例は、中間層でのインターフェイス メソッドの実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="53636-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="53636-124">ここでは、次の 2 つの点が重要です。</span><span class="sxs-lookup"><span data-stu-id="53636-124">The following are the two main points to note:</span></span>  
  
-   <span data-ttu-id="53636-125"><xref:System.Data.Linq.DataContext> はメソッドのスコープで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="53636-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
-   <span data-ttu-id="53636-126">メソッドは、実際の結果から成る <xref:System.Collections.IEnumerable> コレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="53636-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="53636-127">シリアライザーは、結果をクライアント/プレゼンテーション層に戻すためのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="53636-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="53636-128">中間層でクエリ結果にローカルにアクセスするには、クエリ変数に対して `ToList` または `ToArray` を呼び出すことで、実行を強制できます。</span><span class="sxs-lookup"><span data-stu-id="53636-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="53636-129">その後、そのリストまたは配列を `IEnumerable` として返すことができます。</span><span class="sxs-lookup"><span data-stu-id="53636-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =   
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();   
}  
```  
  
 <span data-ttu-id="53636-130">データ コンテキストの 1 つのインスタンスの有効期間は、1 つの「作業単位」である必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="53636-131">疎結合環境では、通常、作業単位は小さく、たとえば `SubmitChanges` の 1 つの呼び出しを含む単一のオプティミスティック トランザクションです。</span><span class="sxs-lookup"><span data-stu-id="53636-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="53636-132">このため、データ コンテキストはメソッドのスコープ内で作成されて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="53636-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="53636-133">作業単位にビジネス ルール ロジックの呼び出しが含まれる場合、通常は、その操作全体のために `DataContext` インスタンスを保持する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="53636-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="53636-134">いずれにしても、`DataContext` インスタンスの有効期間は、多数のトランザクションにわたって長い時間になることが意図されていません。</span><span class="sxs-lookup"><span data-stu-id="53636-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="53636-135">このメソッドは Product オブジェクトを返しますが、各 Product に関連付けられた Order_Detail オブジェクトのコレクションを返しません。</span><span class="sxs-lookup"><span data-stu-id="53636-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="53636-136">この既定の動作を変更するには、<xref:System.Data.Linq.DataLoadOptions> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="53636-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="53636-137">詳細については、次を参照してください。[する方法: コントロールより関連データの取得方法](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="53636-138">データの挿入</span><span class="sxs-lookup"><span data-stu-id="53636-138">Inserting Data</span></span>  
 <span data-ttu-id="53636-139">新しいオブジェクトを挿入するために、プレゼンテーション層は単に中間層インターフェイス上の関連するメソッドを呼び出して、挿入対象の新しいオブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="53636-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="53636-140">ただし、クライアントがいくつかの値だけを渡して、オブジェクト全体の構築を中間層に任せた方が効率的である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="53636-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="53636-141">中間層での実装</span><span class="sxs-lookup"><span data-stu-id="53636-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="53636-142">中間層で、新しい <xref:System.Data.Linq.DataContext> が作成され、<xref:System.Data.Linq.DataContext> メソッドを使ってオブジェクトが <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> にアタッチされて、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出し時にオブジェクトが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="53636-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="53636-143">他の Web サービスのシナリオとまったく同じ方法で、例外、コールバック、エラー状態を処理できます。</span><span class="sxs-lookup"><span data-stu-id="53636-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="53636-144">データの削除</span><span class="sxs-lookup"><span data-stu-id="53636-144">Deleting Data</span></span>  
 <span data-ttu-id="53636-145">既存のオブジェクトをデータベースから削除するために、プレゼンテーション層は中間層インターフェイス上の関連するメソッドを呼び出して、削除対象のオブジェクトの元の値を含むコピーを渡します。</span><span class="sxs-lookup"><span data-stu-id="53636-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="53636-146">削除操作ではオプティミスティック同時実行制御チェックが行われて、削除対象のオブジェクトを新しいデータ コンテキストに最初にアタッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="53636-147">この例では、オブジェクトにタイムスタンプ (RowVersion) が含まれないことを示すために `Boolean` パラメーターが `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="53636-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="53636-148">各レコードのタイムスタンプがデータベース テーブルで生成される場合には、同時実行チェックは特にクライアントにとって非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="53636-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="53636-149">元のオブジェクトまたは変更後のオブジェクトを渡して、`Boolean` パラメーターを `true` に設定するだけです。</span><span class="sxs-lookup"><span data-stu-id="53636-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="53636-150">いずれの場合も、中間層では、通常、<xref:System.Data.Linq.ChangeConflictException> をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="53636-151">オプティミスティック同時実行の競合を処理する方法の詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="53636-152">関連するテーブルに対する外部キー制約を含むエンティティを削除する際には、<xref:System.Data.Linq.EntitySet%601> コレクション内のすべてのオブジェクトを最初に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="53636-153">データの更新</span><span class="sxs-lookup"><span data-stu-id="53636-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="53636-154"> は、オプティミスティック同時実行制御を行う次のようなシナリオでの更新をサポートします。</span><span class="sxs-lookup"><span data-stu-id="53636-154"> supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
-   <span data-ttu-id="53636-155">タイムスタンプつまり RowVersion 番号に基づくオプティミスティック同時実行制御。</span><span class="sxs-lookup"><span data-stu-id="53636-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
-   <span data-ttu-id="53636-156">エンティティ プロパティのサブセットの元の値に基づくオプティミスティック同時実行制御。</span><span class="sxs-lookup"><span data-stu-id="53636-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
-   <span data-ttu-id="53636-157">元のエンティティ全体および変更後のエンティティ全体に基づくオプティミスティック同時実行制御。</span><span class="sxs-lookup"><span data-stu-id="53636-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="53636-158">また、エンティティとそのリレーションシップの両方に対して更新または削除を実行することもできます (たとえば Customer と、それに関連した Order オブジェクトのコレクション)。</span><span class="sxs-lookup"><span data-stu-id="53636-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="53636-159">エンティティ オブジェクトとその子 (`EntitySet`) コレクションから成るグラフをクライアント上で変更して、オプティミスティック同時実行制御チェックで元の値が必要とされる場合には、クライアントはそれぞれのエンティティと <xref:System.Data.Linq.EntitySet%601> オブジェクトの元の値を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="53636-160">1 つのメソッド呼び出しで互いに関連する更新、削除、挿入のセットをクライアントが実行できるようにするには、各エンティティにどんな操作を実行するかを示す方法をクライアントに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="53636-161">その後、中間層で適切な <xref:System.Data.Linq.ITable.Attach%2A> メソッドを呼び出した後、<xref:System.Data.Linq.ITable.InsertOnSubmit%2A> を呼び出す前に、各エンティティに対して <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> または `Attach` (挿入の場合は <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 無し) を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="53636-162">更新を試行する前に元の値を入手するためにデータベースからデータを取得しないでください。</span><span class="sxs-lookup"><span data-stu-id="53636-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="53636-163">オプティミスティック同時実行制御の詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="53636-164">詳細については、オプティミスティック同時実行制御を解決する競合は、「[する方法: 変更の競合の管理](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="53636-165">それぞれのシナリオの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="53636-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="53636-166">タイムスタンプを使用したオプティミスティック同時実行</span><span class="sxs-lookup"><span data-stu-id="53636-166">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="53636-167">元の値のサブセットを使用した場合</span><span class="sxs-lookup"><span data-stu-id="53636-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="53636-168">この手法では、クライアントは変更対象の値と共に、シリアル化されたオブジェクト全体を返します。</span><span class="sxs-lookup"><span data-stu-id="53636-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="53636-169">エンティティ全体を使用する場合</span><span class="sxs-lookup"><span data-stu-id="53636-169">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }   
    }  
}  
```  
  
 <span data-ttu-id="53636-170">コレクションを更新するには、<xref:System.Data.Linq.ITable.AttachAll%2A> ではなく `Attach` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53636-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="53636-171">必要なエンティティ メンバー</span><span class="sxs-lookup"><span data-stu-id="53636-171">Expected Entity Members</span></span>  
 <span data-ttu-id="53636-172">既に説明したように、`Attach` メソッドを呼び出す前に設定する必要があるのは、エンティティ オブジェクトのいくつかのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="53636-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="53636-173">設定する必要のあるエンティティ メンバーは、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
-   <span data-ttu-id="53636-174">エンティティの ID の一部分である。</span><span class="sxs-lookup"><span data-stu-id="53636-174">Be part of the entity’s identity.</span></span>  
  
-   <span data-ttu-id="53636-175">変更される予定である。</span><span class="sxs-lookup"><span data-stu-id="53636-175">Be expected to be modified.</span></span>  
  
-   <span data-ttu-id="53636-176">タイムスタンプであるか、<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性が `Never` 以外の値に設定されている。</span><span class="sxs-lookup"><span data-stu-id="53636-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="53636-177">テーブルでオプティミスティック同時実行チェック用にタイムスタンプまたはバージョン番号を使用している場合は、<xref:System.Data.Linq.ITable.Attach%2A> を呼び出す前にこれらのメンバーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="53636-178">Column 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> プロパティが true に設定されている場合、メンバーはオプティミスティック同時実行チェック専用です。</span><span class="sxs-lookup"><span data-stu-id="53636-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="53636-179">要求された更新は、データベース上のバージョン番号またはタイムスタンプ値が同じ場合にのみ、送信されます。</span><span class="sxs-lookup"><span data-stu-id="53636-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="53636-180">また、<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> が `Never` に設定されていないメンバーもまた、オプティミスティック同時実行チェックに使用されます。</span><span class="sxs-lookup"><span data-stu-id="53636-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="53636-181">他の値が指定されない場合、既定値は `Always` です。</span><span class="sxs-lookup"><span data-stu-id="53636-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="53636-182">これらの必要なメンバーのいずれかが欠落している場合、<xref:System.Data.Linq.ChangeConflictException> 中に <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("行が見つからないか変更されています") がスローされます。</span><span class="sxs-lookup"><span data-stu-id="53636-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="53636-183">状態</span><span class="sxs-lookup"><span data-stu-id="53636-183">State</span></span>  
 <span data-ttu-id="53636-184">エンティティ オブジェクトが <xref:System.Data.Linq.DataContext> インスタンスにアタッチされた後、そのオブジェクトは `PossiblyModified` 状態にあると見なされます。</span><span class="sxs-lookup"><span data-stu-id="53636-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="53636-185">アタッチされたオブジェクトを強制的に `Modified` 状態にする方法は、3 つあります。</span><span class="sxs-lookup"><span data-stu-id="53636-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1.  <span data-ttu-id="53636-186">未変更としてアタッチした後、フィールドを直接変更する。</span><span class="sxs-lookup"><span data-stu-id="53636-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2.  <span data-ttu-id="53636-187">現在のオブジェクト インスタンスと元のオブジェクト インスタンスを受け入れる <xref:System.Data.Linq.Table%601.Attach%2A> オーバーロードを使ってアタッチする。</span><span class="sxs-lookup"><span data-stu-id="53636-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="53636-188">こうすると、古い値と新しい値が変更トラッカーに提供されるため、変更されたフィールドが自動的に判別されます。</span><span class="sxs-lookup"><span data-stu-id="53636-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3.  <span data-ttu-id="53636-189">(true に設定された) 2 番目のブール値パラメーターを受け入れる <xref:System.Data.Linq.Table%601.Attach%2A> オーバーロードを使ってアタッチする。</span><span class="sxs-lookup"><span data-stu-id="53636-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="53636-190">こうすると、元の値を提供しなくても、変更トラッカーはオブジェクトが変更済みと見なします。</span><span class="sxs-lookup"><span data-stu-id="53636-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="53636-191">この手法では、オブジェクトにバージョン/タイムスタンプ フィールドが含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="53636-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="53636-192">詳細については、次を参照してください。[オブジェクトの状態と変更の追跡](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md)です。</span><span class="sxs-lookup"><span data-stu-id="53636-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="53636-193">アタッチ対象のオブジェクトと同じ ID を持つエンティティ オブジェクトが ID キャッシュ内に既に存在する場合、<xref:System.Data.Linq.DuplicateKeyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="53636-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="53636-194">オブジェクトの `IEnumerable` セットを使ってアタッチするとき、既存のキーが含まれる場合には、<xref:System.Data.Linq.DuplicateKeyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="53636-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="53636-195">残りのオブジェクトはアタッチされません。</span><span class="sxs-lookup"><span data-stu-id="53636-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53636-196">参照</span><span class="sxs-lookup"><span data-stu-id="53636-196">See Also</span></span>  
 [<span data-ttu-id="53636-197">LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション</span><span class="sxs-lookup"><span data-stu-id="53636-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [<span data-ttu-id="53636-198">背景情報</span><span class="sxs-lookup"><span data-stu-id="53636-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
