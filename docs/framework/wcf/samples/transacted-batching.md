---
title: "トランザクション バッチ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc04f0ce1d303a32cbf2232c76bfc4ef1143c9ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-batching"></a>トランザクション バッチ
このサンプルでは、メッセージ キュー (MSMQ) を使用して、トランザクション読み取りをバッチ処理する方法を示します。 トランザクション バッチは、キューを使用する通信でトランザクション読み取りのパフォーマンスを最適化するための機能です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 キュー通信では、クライアントはサービスとの通信にキューを使用します。 厳密には、クライアントはメッセージをキューに送信します。 サービスは、メッセージをキューから受信します。 したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。  
  
 このサンプルでは、トランザクション バッチを示します。 トランザクション バッチの動作では、キューに置かれた多数のメッセージを読み取ってそれを処理するために使用するトランザクションが 1 つで済みます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。 キューが存在しない場合、サービスによってキューが作成されます。 最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。 Windows 2008 でキューを作成するには、次の手順に従います。  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。  
  
    2.  展開して、**機能**タブです。  
  
    3.  右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。  
  
    4.  チェック、**トランザクション**ボックス。  
  
    5.  入力`ServiceModelSamplesTransacted`として、新しいキューの名前。  
  
    > [!NOTE]
    >  このサンプルでは、クライアントは多数のメッセージをバッチの一部として送信します。 通常、サービス アプリケーションがこれらを処理するのに多少の時間がかかります。  
  
3.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>ワークグループに属しているコンピューターまたは Active Directory 統合のないコンピューターでこのサンプルを実行するには  
  
1.  <xref:System.ServiceModel.NetMsmqBinding> を使用する場合の既定では、トランスポート セキュリティが有効です。 MSMQ トランスポート セキュリティでは、2 つの関連するプロパティがある<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>と<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`既定では、認証モードに設定`Windows`保護レベルに設定されていると`Sign`です。 MSMQ の認証機能と署名機能を利用するには、ドメインに MSMQ があることと、MSMQ に関する Active Directory の統合オプションがインストールされていることが必要です。 この条件を満たしていないコンピューターでこのサンプルを実行すると、エラーになります。  
  
2.  ドメインに属していないコンピュータ、または Active Directory 統合がインストールされていないコンピュータを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを `None` にします。この構成の例を次に示します。  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  サーバーとクライアントの両方の構成を変更したことを確認してから、サンプルを実行します。  
  
    > [!NOTE]
    >  `security``mode` を `None` に設定することは、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>、および `Message` のセキュリティを `None` に設定することに相当します。  
  
4.  データベースをリモート コンピューターで実行するには、接続文字列をデータベースが存在するコンピューターを指すように変更します。  
  
## <a name="requirements"></a>要件  
 このサンプルを実行するには、MSMQ をインストールする必要があります。さらに、SQL または SQL Express が必要です。  
  
## <a name="demonstrates"></a>使用例  
 このサンプルはトランザクション バッチ動作を示します。 トランザクション バッチは、MSMQ キューを使用したトランスポートで提供されるパフォーマンス最適化機能です。  
  
 メッセージの送受信にトランザクションが使用されている場合、実際には 2 つの別個のトランザクションが存在しています。 クライアントがトランザクションのスコープ内でメッセージを送信する場合、トランザクションはクライアントおよびクライアント キュー マネージャにとってローカルとなります。 サービスがトランザクションのスコープ内でメッセージを受信する場合、トランザクションはサービスおよび受信キュー マネージャにとってローカルとなります。 クライアントとサービスは同じトランザクションに参加していません。むしろ、キューに対して操作 (送信や受信など) を実行する場合は異なるトランザクションを使用することに注意してください。  
  
 このサンプルでは、複数のサービス操作を実行する際に単一のトランザクションを使用します。 これはパフォーマンス最適化機能としてのみ使用されるもので、アプリケーションのセマンティクスには影響しません。 サンプルがに基づいて[トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)です。  
  
## <a name="comments"></a>コメント  
 このサンプルでは、クライアントはトランザクションのスコープ内からメッセージのバッチをサービスに送信します。 パフォーマンスの最適化を示すために、この例では最大 2,500 という多数のメッセージを送信します。  
  
 キューに送信されたメッセージは、サービスによって定義されたトランザクション スコープ内のサービスによって受信されます。 バッチ処理が行われない場合、2,500 のトランザクションが実行され、そのたびにサービス操作が呼び出されます。 これはシステムのパフォーマンスに影響します。 MSMQ キューと `Orders` データベースという 2 つのリソース マネージャが含まれているので、このようなトランザクションはそれぞれ DTC トランザクションです。 これを最適化するには、単一のトランザクション内でメッセージとサービス操作の呼び出しのバッチを発生させることによって、使用するトランザクション数を大幅に減らします。  
  
 次の手順により、バッチ機能を使用します。  
  
-   トランザクション バッチ動作を構成で指定します。  
  
-   単一のトランザクションを使用していくつのメッセージを読み取るかという観点から、バッチ サイズを指定します。  
  
-   同時に実行するバッチの最大数を指定します。  
  
 この例では、100 のサービス操作を単一のトランザクションで呼び出してからトランザクションをコミットするという方法でトランザクションの数を減らすことにより、パフォーマンスの向上を示します。  
  
 サービス動作は、`TransactionScopeRequired` が `true` に設定された操作動作を定義します。 これにより、キューからのメッセージの取得に使用されるものと同じトランザクション スコープが、このメソッドによってアクセスされる任意のリソース マネージャにより使用されます。 この例では、基本的なデータベースを使用してメッセージに含まれる発注書情報を保存します。 さらにトランザクション スコープでは、メソッドから例外がスローされた場合にメッセージがキューに返されることも保証されます。 このサービス動作を設定しない場合、キューに置かれたチャネルはトランザクションを作成して、キューからのメッセージを読み取り、操作が失敗した場合には、ディスパッチによってメッセージが失われる前に、自動的にそのメッセージをコミットします。 最もよく見られるシナリオは、キューからのメッセージの読み込みに使用するトランザクションにサービス操作を登録することです。次のコードを参照してください。  
  
 `ReleaseServiceInstanceOnTransactionComplete` が `false` に設定されていることに注意してください。 これはバッチ処理の重要な要件です。 `ReleaseServiceInstanceOnTransactionComplete` のプロパティ `ServiceBehaviorAttribute` は、トランザクションが完了した後のサービス インスタンスの処理方法を示します。 既定では、トランザクションが完了するとサービス インスタンスは解放されます。 バッチ処理の主な特徴は、キューに置かれた多数のメッセージを読み取ってディスパッチするために単一のトランザクションを使用する点です。 そのため、サービス インスタンスが解放されると、実際にバッチ処理が行われる前にトランザクションが完了することになります。 このプロパティが `true` に設定され、トランザクション バッチ動作がエンドポイントに追加された場合、このバッチ処理の検証動作は例外をスローします。  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 `Orders` クラスは、注文処理機能をカプセル化します。 サンプルでは、このクラスは発注書情報を使用してデータベースを更新します。  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 バッチ動作とその構成は、サービス アプリケーションの構成で指定されます。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  バッチ サイズにより、システムの動作が決まります。 たとえば、バッチ サイズを 20 に指定した場合、20 のメッセージが単一トランザクションを使用して読み取られてディスパッチされ、その後トランザクションがコミットされます。 しかし、そのバッチ サイズに達する前にトランザクションがバッチをコミットする場合もあります。  
>   
>  各トランザクションにはタイムアウトが関連付けられています。これはトランザクションが作成された後に時間刻みを開始します。 このタイムアウト時間が経過すると、トランザクションは中止されます。 バッチ サイズに達していなくてもタイムアウト時間が経過する可能性があります。 中止された後でバッチを再動作させないようにするため、`TransactedBatchingBehavior` はトランザクションの残り時間を確認します。 トランザクションのタイムアウトが 80% 経過すると、トランザクションはコミットされます。  
>   
>  キューのメッセージがなくなると、<xref:System.ServiceModel.Description.TransactedBatchingBehavior> はバッチ サイズに達するまで待機する代わりに、トランザクションをコミットします。  
>   
>  バッチ サイズの選択は、アプリケーションに依存します。 バッチ サイズが小さすぎると、必要なパフォーマンスを実現できません。 逆にバッチ サイズが大きすぎると、パフォーマンスが低下する場合があります。 たとえば、トランザクションが長期間有効でデータベースのロックを保持したり、またはトランザクションがデッドロック状態になる場合があります。この場合、バッチはロール バックされて作業がやり直しになる可能性があります。  
  
 クライアントはトランザクション スコープを作成します。 キューとの通信はトランザクションのスコープ内で実行されるため、すべてのメッセージがキューに送信されるか、またはメッセージがキューにまったく送信されないかを示す、アトミック単位として扱われます。 トランザクションは、トランザクション スコープで <xref:System.Transactions.TransactionScope.Complete%2A> を呼び出すことでコミットされます。  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。 サービスがクライアントから受信したメッセージを表示できます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。 キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。 クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。 メッセージがバッチ内で読み取られて処理された際には、ロール出力を表示できます。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>関連項目
