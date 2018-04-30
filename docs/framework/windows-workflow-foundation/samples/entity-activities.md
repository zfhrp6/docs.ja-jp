---
title: エンティティ アクティビティ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff7e505f6e2040e847b711030d310a70ede65413
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="entity-activities"></a><span data-ttu-id="d1c3a-102">エンティティ アクティビティ</span><span class="sxs-lookup"><span data-stu-id="d1c3a-102">Entity Activities</span></span>
<span data-ttu-id="d1c3a-103">このサンプルでは、Windows Workflow Foundation と ADO.NET Entity Framework を使用して、データ アクセスを簡素化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-103">This sample shows how to use the ADO.NET Entity Framework with Windows Workflow Foundation to simplify data access.</span></span>  
  
 <span data-ttu-id="d1c3a-104">ADO.NET Entity Framework を使用すると、開発者は、ドメイン固有のオブジェクト、プロパティ、およびリレーションシップ (Customers、Orders、Order Details、およびこれらのエンティティ間のリレーションシップなど) の形式でデータを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="d1c3a-105">ADO.NET Entity Framework では、この機能を実現するために、リレーショナル ストレージ スキーマに対して直接プログラムを作成するのではなく、概念アプリケーション モデルに対してプログラムを作成できる抽象化レベルを提供します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> <span data-ttu-id="d1c3a-106">詳細については、ADO.NET Entity Framework を参照してください[ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549)です。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-106">For more information about the ADO.NET Entity Framework see [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d1c3a-107">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="d1c3a-107">Sample details</span></span>  
 <span data-ttu-id="d1c3a-108">このサンプルでは、`Northwind` データベースを使用します。また、`Northwind` データベースを作成および削除するためのスクリプトが用意されています (Setup.cmd と Cleanup.cmd)。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="d1c3a-109">このサンプルのプロジェクトには、`Northwind` データベースに基づく Entity Data Model が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="d1c3a-110">このモデルは、プロジェクトに含まれている `Northwind.edmx` ファイルを開くことで見つかります。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="d1c3a-111">これは、ADO.NET Entity Framework を使用してアクセスできるオブジェクトの形状を定義するモデルです。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="d1c3a-112">このサンプルには、次のアクティビティがあります。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="d1c3a-113">`EntitySQLQuery`: `EntitySQLQuery` アクティビティを使用すると、Entity SQL クエリ文字列に基づいてデータベースからオブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="d1c3a-114">Entity SQL はストレージに依存しない SQL と似たクエリ言語です。この言語では、概念モデルに基づいて、またモデルまたはドメインの一部であるエンティティに基づいて、クエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> <span data-ttu-id="d1c3a-115">Entity SQL 言語の詳細については、次を参照してください。 [Entity SQL 言語](http://go.microsoft.com/fwlink/?LinkId=165646)します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-115">For more information about Entity SQL Language, see [Entity SQL Language](http://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="d1c3a-116">`EntityLinqQuery`: このアクティビティを使用すると、LINQ クエリまたは LINQ 述語に基づいてデータベースからオブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="d1c3a-117">`EntityAdd`: `EntityAdd` アクティビティを使用すると、エンティティまたはエンティティのコレクションをデータベースに追加できます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="d1c3a-118">`EntityDelete`: `EntityDelete` アクティビティを使用すると、エンティティまたはエンティティのコレクションをデータベースから削除できます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="d1c3a-119">`ObjectContextScope`: 前に説明した各アクティビティは、これらを格納する `ObjectContextScope` アクティビティ インスタンス内でしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="d1c3a-120">`ObjectContextScope` アクティビティは、データベースへの接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="d1c3a-121">これには接続文字列が必要です (接続文字列は、構成ファイルの設定を使用して渡すか取得します)。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="d1c3a-122">`ObjectContextScope` アクティビティにより、エンティティに対して、関連する操作のグループを簡単に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="d1c3a-123">このスコープはアクティブな接続を維持するので、非永続的スコープです。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="d1c3a-124">また、`ObjectContextScope` アクティビティが存在する場合、そのスコープ内でエンティティ アクティビティを使用して取得したオブジェクトに対する変更は、データベースに自動的に永続化され、オブジェクトをデータベースに保存するのに明示的な操作や追加の操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="d1c3a-125">エンティティ アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="d1c3a-125">Using the entity activities</span></span>  
 <span data-ttu-id="d1c3a-126">以下の各コード スニペットは、このサンプルに含まれているエンティティ アクティビティを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="d1c3a-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="d1c3a-127">EntitySql</span></span>  
 <span data-ttu-id="d1c3a-128">次のコード スニペットは、ロンドン在住のすべての顧客を照会して名前で並べ替える方法、および顧客のリストを反復処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a><span data-ttu-id="d1c3a-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="d1c3a-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="d1c3a-130">次のコード スニペットは、ロンドン在住のすべての顧客を照会する方法、および結果として得られた顧客のリストを反復処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a><span data-ttu-id="d1c3a-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="d1c3a-131">EntityAdd</span></span>  
 <span data-ttu-id="d1c3a-132">次のコード スニペットは、OrderDetail レコードを既存の Order に追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a><span data-ttu-id="d1c3a-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="d1c3a-133">EntityDelete</span></span>  
 <span data-ttu-id="d1c3a-134">次のコード スニペットは、Order の既存の OrderDetail レコードを削除する方法を示しています (OrderDetail レコードがある場合)。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="d1c3a-135">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="d1c3a-135">To use this sample</span></span>  
 <span data-ttu-id="d1c3a-136">このサンプルを実行する前に、SQL Server Express のローカル インスタンスに `Northwind` データベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="d1c3a-137">Northwind データベースを設定するには</span><span class="sxs-lookup"><span data-stu-id="d1c3a-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="d1c3a-138">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="d1c3a-139">新しいコマンド プロンプト ウィンドウで、EntityActivities\CS フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="d1c3a-140">型`setup.cmd`ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="d1c3a-141">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="d1c3a-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="d1c3a-142">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EntityActivities.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d1c3a-143">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d1c3a-144">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="d1c3a-145">このサンプルの実行後、`Northwind` データベースの削除が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="d1c3a-146">Northwind データベースをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="d1c3a-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="d1c3a-147">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="d1c3a-148">新しいコマンド プロンプト ウィンドウで、EntityActivities\CS フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="d1c3a-149">型`cleanup.cmd`ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1c3a-150">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d1c3a-151">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d1c3a-152">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1c3a-153">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1c3a-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`