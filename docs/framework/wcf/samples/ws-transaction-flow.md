---
title: "WS トランザクション フロー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
caps.latest.revision: "43"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7043956427561e4485bdad6a98673b997bc88e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="69a92-102">WS トランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="69a92-102">WS Transaction Flow</span></span>
<span data-ttu-id="69a92-103">このサンプルでは、クライアントによって調整されるトランザクションの使用方法と、WS-AtomicTransaction プロトコルまたは OleTransactions プロトコルを使用するトランザクション フローに関するクライアントとサーバーのオプションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="69a92-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="69a92-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)、電卓サービスを実装するが、操作の属性が設定の使用をデモ、`TransactionFlowAttribute`で、 **TransactionFlowOption**どの程度トランザクションをフローが有効になっているを決定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="69a92-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="69a92-105">フローされたトランザクションのスコープ内では、要求された操作のログがデータベースに書き込まれ、クライアント調整トランザクションが完了するまで保持されます。クライアント トランザクションが完了しない場合は、データベースに対する該当する更新はコミットされません。</span><span class="sxs-lookup"><span data-stu-id="69a92-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a92-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a92-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="69a92-107">サービスとトランザクションへの接続を開始した後で、クライアントは複数のサービス操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="69a92-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="69a92-108">サービスのコントラクトは次のように定義されています。操作はそれぞれ、`TransactionFlowOption` の設定が異なります。</span><span class="sxs-lookup"><span data-stu-id="69a92-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```  
  
 <span data-ttu-id="69a92-109">操作は、処理される順に次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="69a92-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="69a92-110">`Add` (加算) 操作要求には、フローされたトランザクションが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a92-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="69a92-111">`Subtract` (減算) 操作要求には、フローされたトランザクションが含まれていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="69a92-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="69a92-112">`Multiply` (乗算) 操作要求には、フローされたトランザクションが含まれてはならないことが、明示的な NotAllowed 設定で指定されています。</span><span class="sxs-lookup"><span data-stu-id="69a92-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="69a92-113">`Divide` (除算) 操作要求には、フローされたトランザクションが含まれてはならないことが、`TransactionFlow` 属性の省略によって指定されています。</span><span class="sxs-lookup"><span data-stu-id="69a92-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="69a92-114">トランザクション フローを使用したバインディングで有効にする、 [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)属性に加えて、適切な操作有効になっているプロパティを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a92-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="69a92-115">このサンプルでは、サービスの構成は Metadata Exchange エンドポイントのほかに TCP エンドポイントと HTTP エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="69a92-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="69a92-116">TCP エンドポイントと HTTP エンドポイントがどちらも次のバインディングを使用して、 [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)プロパティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="69a92-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="69a92-117">システムで提供される netTcpBinding では transactionProtocol を指定できるのに対し、システムで提供される wsHttpBinding では、相互運用性に優れた WSAtomicTransactionOctober2004 プロトコルのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="69a92-118">OleTransactions プロトコルは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントで使用する場合にのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="69a92-118">The OleTransactions protocol is only available for use by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] clients.</span></span>  
  
 <span data-ttu-id="69a92-119">`ICalculator` インターフェイスを実装するクラスでは、すべてのメソッドの属性で <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティが `true` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="69a92-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="69a92-120">この設定は、メソッド内で実行されるすべてのアクションがトランザクションのスコープ内で実行されることを宣言するものです。</span><span class="sxs-lookup"><span data-stu-id="69a92-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="69a92-121">この場合、実行されるアクションには、ログ データベースへの記録が含まれます。</span><span class="sxs-lookup"><span data-stu-id="69a92-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="69a92-122">操作要求の中に、フローされたトランザクションが含まれている場合は、受信トランザクションのスコープ内でアクションが実行されるか、新しいトランザクションが自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a92-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティは、サービス メソッド実装固有の動作を定義しますが、トランザクションをフローさせるためのクライアントの機能や要件は定義しません。</span><span class="sxs-lookup"><span data-stu-id="69a92-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  
  
```  
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```  
  
 <span data-ttu-id="69a92-124">クライアントでは、操作に対するサービスの `TransactionFlowOption` 設定が、クライアントで生成される `ICalculator` インターフェイスの定義に反映されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="69a92-125">さらに、サービスの `transactionFlow` プロパティの設定はクライアントのアプリケーション構成に反映されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="69a92-126">クライアントでは、適切な `endpointConfigurationName` を選択することによってトランスポートとプロトコルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="69a92-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  
  
```  
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```  
  
> [!NOTE]
>  <span data-ttu-id="69a92-127">このサンプルを実行したときの動作は、選択したプロトコルとトランスポートの種類にかかわらず同一です。</span><span class="sxs-lookup"><span data-stu-id="69a92-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="69a92-128">サービスへの接続を開始した後で、クライアントは次のように、サービス操作の呼び出しを囲む新しい `TransactionScope` を作成します。</span><span class="sxs-lookup"><span data-stu-id="69a92-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  
  
```  
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```  
  
 <span data-ttu-id="69a92-129">操作の呼び出しは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="69a92-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="69a92-130">`Add` 要求によって、必須のトランザクションがサービスにフローされ、サービスのアクションはクライアントのトランザクション スコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="69a92-131">最初の `Subtract` 要求も、許可されたトランザクションをサービスにフローするので、このときもサービスのアクションはクライアントのトランザクション スコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="69a92-132">2 番目の `Subtract` 要求は、`TransactionScopeOption.Suppress` オプションと共に宣言された新しいトランザクション スコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="69a92-133">これによって、クライアントの最初の外側トランザクションが抑制されます。また、新しいトランザクションがサービスにフローされることはありません。</span><span class="sxs-lookup"><span data-stu-id="69a92-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="69a92-134">この方法を使用すると、クライアントは、トランザクションをサービスにフローすることが必要ない場合に、このことを行わないように明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="69a92-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="69a92-135">サービスのアクションは、新しい独立したトランザクションのスコープ内で発生します。</span><span class="sxs-lookup"><span data-stu-id="69a92-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="69a92-136">`Multiply` 要求はトランザクションをサービスにフローしません。クライアントで生成された `ICalculator` インターフェイスの定義には <xref:System.ServiceModel.TransactionFlowAttribute><xref:System.ServiceModel.TransactionFlowOption> に設定された `NotAllowed` が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="69a92-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="69a92-137">`Divide` 要求は、トランザクションをサービスにフローしません。同様に、クライアントで生成された `ICalculator` インターフェイスの定義には `TransactionFlowAttribute` が含まれていないためです。</span><span class="sxs-lookup"><span data-stu-id="69a92-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="69a92-138">このときも、サービスのアクションは別の新しい独立したトランザクションのスコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="69a92-139">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="69a92-140">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="69a92-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="69a92-141">サービス操作要求のログ記録は、サービスのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="69a92-142">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="69a92-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="69a92-143">実行が正常に終了すると、クライアントのトランザクション スコープが完了し、そのスコープ内で実行されたすべてのアクションがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="69a92-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="69a92-144">具体的には、ここに示した 5 レコードがサービスのデータベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="69a92-145">最初の 2 レコードは、クライアントのトランザクションのスコープ内で発生しています。</span><span class="sxs-lookup"><span data-stu-id="69a92-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="69a92-146">クライアントの `TransactionScope` 内の場所で例外が発生した場合、トランザクションは完了しません。</span><span class="sxs-lookup"><span data-stu-id="69a92-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="69a92-147">その結果、そのスコープ内でログに記録されたレコードはデータベースにコミットされなくなります。</span><span class="sxs-lookup"><span data-stu-id="69a92-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="69a92-148">この影響を確認するには、外側の `TransactionScope` を完了させる呼び出しをコメント化した後にサンプルをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="69a92-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="69a92-149">この実行では、最後の 3 つのアクション (2 番目の `Subtract` 要求、`Multiply` 要求、`Divide` 要求) だけがログに記録されます。クライアント トランザクションはこれらのアクションにフローしないためです。</span><span class="sxs-lookup"><span data-stu-id="69a92-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69a92-150">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="69a92-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="69a92-151">C# または Visual Basic .NET のバージョンのソリューションをビルドするの指示に従って、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="69a92-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2.  <span data-ttu-id="69a92-152">SQL Server Express Edition または SQL Server がインストールされ、接続文字列が、サービスのアプリケーション構成ファイルで正しく設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="69a92-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="69a92-153">データベースを使用せずにサンプルを実行するには、サービスのアプリケーション構成ファイルで `usingSql` の値を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="69a92-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3.  <span data-ttu-id="69a92-154">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="69a92-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69a92-155">複数コンピューター構成の場合は、次の説明に従って分散トランザクション コーディネーターを有効にし、Windows SDK の WsatConfig.exe ツールを使用して WCF トランザクション ネットワークのサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="69a92-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="69a92-156">参照してください[Ws-atomic Transaction サポートの構成](http://go.microsoft.com/fwlink/?LinkId=190370)WsatConfig.exe を設定する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="69a92-156">See [Configuring WS-Atomic Transaction Support](http://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="69a92-157">サンプルを同じコンピューターまたは複数のコンピューターのどちらで実行する場合も、Microsoft 分散トランザクション コーディネーター (MSDTC) を構成してネットワーク トランザクション フローを有効にし、WsatConfig.exe ツールを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トランザクション ネットワーク サポートを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a92-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="69a92-158">Microsoft 分散トランザクション コーディネーター (MSDTC) を構成してサンプルを実行できるようにするには</span><span class="sxs-lookup"><span data-stu-id="69a92-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1.  <span data-ttu-id="69a92-159">Windows Server 2003 または Windows XP が動作するサービス コンピューターで、次の説明に従い、受信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="69a92-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="69a92-160">**開始** メニューの "éˆú"**コントロール パネルの **、し**管理ツール**、し、**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="69a92-161">展開**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-161">Expand **Component Services**.</span></span> <span data-ttu-id="69a92-162">開く、**コンピューター**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="69a92-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="69a92-163">右クリック**マイ コンピューター**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="69a92-164">**MSDTC**  タブで、をクリックして**セキュリティ構成**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="69a92-165">確認**ネットワーク DTC アクセス**と**を許可する受信**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="69a92-166">をクリックして**[ok]**、順にクリックして**はい**MSDTC サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="69a92-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="69a92-167">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="69a92-167">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="69a92-168">Windows Server 2008 または Windows Vista が動作するサービス コンピューターで、次の説明に従い、受信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="69a92-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="69a92-169">**開始** メニューの "éˆú"**コントロール パネルの **、し**管理ツール**、し、**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="69a92-170">展開**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-170">Expand **Component Services**.</span></span> <span data-ttu-id="69a92-171">開く、**コンピューター**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="69a92-171">Open the **Computers** folder.</span></span> <span data-ttu-id="69a92-172">選択**分散トランザクション コーディネーター**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="69a92-173">右クリック**DTC コーディネーター**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="69a92-174">**セキュリティ** タブで、チェック**ネットワーク DTC アクセス**と**受信を許可する**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="69a92-175">をクリックして**[ok]**、順にクリックして**はい**MSDTC サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="69a92-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="69a92-176">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="69a92-176">Click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="69a92-177">クライアント コンピューターで、送信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="69a92-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="69a92-178">**開始** メニューに移動`Control Panel`、し**管理ツール**、し**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="69a92-179">右クリック**マイ コンピューター**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="69a92-180">**MSDTC**  タブで、をクリックして**セキュリティ構成**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="69a92-181">確認**ネットワーク DTC アクセス**と**送信を許可する**です。</span><span class="sxs-lookup"><span data-stu-id="69a92-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="69a92-182">をクリックして**[ok]**、順にクリックして**はい**MSDTC サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="69a92-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="69a92-183">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="69a92-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69a92-184">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="69a92-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="69a92-185">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="69a92-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="69a92-186">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="69a92-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69a92-187">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="69a92-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
