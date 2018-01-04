---
title: "エンティティ アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c507c3da7f4583bf6ffb7b869cecbf0bfd305077
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="entity-activities"></a>エンティティ アクティビティ
このサンプルでは、ADO.NET Entity Framework と [!INCLUDE[wf2](../../../../includes/wf2-md.md)] を使用してデータ アクセスを簡素化する方法を示します。  
  
 ADO.NET Entity Framework を使用すると、開発者は、ドメイン固有のオブジェクト、プロパティ、およびリレーションシップ (Customers、Orders、Order Details、およびこれらのエンティティ間のリレーションシップなど) の形式でデータを扱うことができます。 ADO.NET Entity Framework では、この機能を実現するために、リレーショナル ストレージ スキーマに対して直接プログラムを作成するのではなく、概念アプリケーション モデルに対してプログラムを作成できる抽象化レベルを提供します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ADO.NET Entity Framework を参照してください[ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549)です。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルでは、`Northwind` データベースを使用します。また、`Northwind` データベースを作成および削除するためのスクリプトが用意されています (Setup.cmd と Cleanup.cmd)。 このサンプルのプロジェクトには、`Northwind` データベースに基づく Entity Data Model が含まれています。 このモデルは、プロジェクトに含まれている `Northwind.edmx` ファイルを開くことで見つかります。 これは、ADO.NET Entity Framework を使用してアクセスできるオブジェクトの形状を定義するモデルです。  
  
 このサンプルには、次のアクティビティがあります。  
  
-   `EntitySQLQuery`: `EntitySQLQuery` アクティビティを使用すると、Entity SQL クエリ文字列に基づいてデータベースからオブジェクトを取得できます。 Entity SQL はストレージに依存しない SQL と似たクエリ言語です。この言語では、概念モデルに基づいて、またモデルまたはドメインの一部であるエンティティに基づいて、クエリを指定できます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Entity SQL 言語を参照してください[Entity SQL 言語](http://go.microsoft.com/fwlink/?LinkId=165646)します。  
  
-   `EntityLinqQuery`: このアクティビティを使用すると、LINQ クエリまたは LINQ 述語に基づいてデータベースからオブジェクトを取得できます。  
  
-   `EntityAdd`: `EntityAdd` アクティビティを使用すると、エンティティまたはエンティティのコレクションをデータベースに追加できます。  
  
-   `EntityDelete`: `EntityDelete` アクティビティを使用すると、エンティティまたはエンティティのコレクションをデータベースから削除できます。  
  
-   `ObjectContextScope`: 前に説明した各アクティビティは、これらを格納する `ObjectContextScope` アクティビティ インスタンス内でしか使用できません。 `ObjectContextScope` アクティビティは、データベースへの接続を設定します。 これには接続文字列が必要です (接続文字列は、構成ファイルの設定を使用して渡すか取得します)。 `ObjectContextScope` アクティビティにより、エンティティに対して、関連する操作のグループを簡単に実行できるようになります。 このスコープはアクティブな接続を維持するので、非永続的スコープです。 また、`ObjectContextScope` アクティビティが存在する場合、そのスコープ内でエンティティ アクティビティを使用して取得したオブジェクトに対する変更は、データベースに自動的に永続化され、オブジェクトをデータベースに保存するのに明示的な操作や追加の操作は必要ありません。  
  
## <a name="using-the-entity-activities"></a>エンティティ アクティビティの使用  
 以下の各コード スニペットは、このサンプルに含まれているエンティティ アクティビティを使用する方法を示しています。  
  
### <a name="entitysql"></a>EntitySql  
 次のコード スニペットは、ロンドン在住のすべての顧客を照会して名前で並べ替える方法、および顧客のリストを反復処理する方法を示しています。  
  
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
  
### <a name="entitylinqquery"></a>EntityLinqQuery  
 次のコード スニペットは、ロンドン在住のすべての顧客を照会する方法、および結果として得られた顧客のリストを反復処理する方法を示しています。  
  
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
  
### <a name="entityadd"></a>EntityAdd  
 次のコード スニペットは、OrderDetail レコードを既存の Order に追加する方法を示しています。  
  
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
  
### <a name="entitydelete"></a>EntityDelete  
 次のコード スニペットは、Order の既存の OrderDetail レコードを削除する方法を示しています (OrderDetail レコードがある場合)。  
  
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
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
 このサンプルを実行する前に、SQL Server Express のローカル インスタンスに `Northwind` データベースを作成する必要があります。  
  
#### <a name="to-set-up-the-northwind-database"></a>Northwind データベースを設定するには  
  
1.  コマンド プロンプトを開きます。  
  
2.  新しいコマンド プロンプト ウィンドウで、EntityActivities\CS フォルダーに移動します。  
  
3.  型`setup.cmd`ENTER キーを押します。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EntityActivities.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
 このサンプルの実行後、`Northwind` データベースの削除が必要になる場合があります。  
  
#### <a name="to-uninstall-the-northwind-database"></a>Northwind データベースをアンインストールするには  
  
1.  コマンド プロンプトを開きます。  
  
2.  新しいコマンド プロンプト ウィンドウで、EntityActivities\CS フォルダーに移動します。  
  
3.  型`cleanup.cmd`ENTER キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`