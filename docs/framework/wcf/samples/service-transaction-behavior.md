---
title: "サービス トランザクションの動作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d881e7727c002cc9cc5322881a67dcb9a780efa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="7840b-102">サービス トランザクションの動作</span><span class="sxs-lookup"><span data-stu-id="7840b-102">Service Transaction Behavior</span></span>
<span data-ttu-id="7840b-103">このサンプルでは、クライアント調整トランザクションの使用方法と、サービス トランザクションの動作を制御する ServiceBehaviorAttribute と OperationBehaviorAttribute の設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7840b-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="7840b-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装しますが、データベース テーブルと、電卓操作の合計を実行しているステートフルで実行される操作のサーバー ログを維持するために拡張されています。</span><span class="sxs-lookup"><span data-stu-id="7840b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="7840b-105">サーバー ログ テーブルへの書き込みを保存するかどうかは、クライアント調整トランザクションの結果によって異なります。クライアント トランザクションが完了しない場合は、Web サービス トランザクションにより、データベースへの更新はコミットされません。</span><span class="sxs-lookup"><span data-stu-id="7840b-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7840b-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7840b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7840b-107">サービスのコントラクトでは、すべての操作でトランザクションを要求に応じてフローする必要があることを、次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="7840b-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 <span data-ttu-id="7840b-108">受信トランザクション フローを有効にするには、transactionFlow 属性が `true` に設定されているシステム指定の wsHttpBinding を使用して、サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="7840b-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="7840b-109">このバインディングは、相互操作可能な WSAtomicTransactionOctober2004 プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="7840b-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="7840b-110">サービスへの接続とトランザクションの起動後、クライアントは次のようにそのトランザクションのスコープに含まれるいくつかのサービス処理にアクセスして、そのトランザクションを完了して接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="7840b-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
```  
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="7840b-111">サービス側には、次のようにサービス トランザクションの動作に影響を及ぼす 3 つの属性があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="7840b-112">`ServiceBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="7840b-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="7840b-113">`TransactionTimeout` プロパティは、トランザクションが完了する必要のある期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="7840b-114">このサンプルでは、30 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7840b-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="7840b-115">`TransactionIsolationLevel` プロパティは、サービスがサポートする分離レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="7840b-116">クライアントの分離レベルと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="7840b-117">`ReleaseServiceInstanceOnTransactionComplete` プロパティは、トランザクションが完了したときにサービス インスタンスを再利用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="7840b-118">`false` に設定すると、サービスは操作要求全体で同じサービス インスタンスを保持します。</span><span class="sxs-lookup"><span data-stu-id="7840b-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="7840b-119">この設定は、現在高を保持するために必要です。</span><span class="sxs-lookup"><span data-stu-id="7840b-119">This is required to maintain the running total.</span></span> <span data-ttu-id="7840b-120">`true` に設定すると、各アクションが完了するたびに新しいインスタンスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7840b-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="7840b-121">`TransactionAutoCompleteOnSessionClose` プロパティは、セッションの終了時に未解決のトランザクションを完了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="7840b-122">設定することによって`false`、個々 の操作が設定するか、`OperationBehaviorAttribute``TransactionAutoComplete`プロパティを`true`またはへの呼び出しを明示的に要求する、`SetTransactionComplete`メソッドがトランザクションを完了します。</span><span class="sxs-lookup"><span data-stu-id="7840b-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="7840b-123">このサンプルでは、両方の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7840b-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="7840b-124">`ServiceContractAttribute` :</span><span class="sxs-lookup"><span data-stu-id="7840b-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="7840b-125">`SessionMode` プロパティは、適切な要求を相互に関連付けて論理セッションに格納するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="7840b-126">このサービスには、OperationBehaviorAttribute TransactionAutoComplete プロパティが `false` に設定されている操作 (乗算および除算) が含まれているため、`SessionMode.Required` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="7840b-127">たとえば、乗算操作ではトランザクションは完了せず、後で呼び出される除算操作により、`SetTransactionComplete` メソッドを使用して完了します。したがってこのサービスでは、これらの操作が同じセッション内で発生するかどうかを決定できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="7840b-128">`OperationBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="7840b-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="7840b-129">`TransactionScopeRequired` プロパティは、操作のアクションをトランザクション スコープ内で実行する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="7840b-130">このプロパティは、このサンプルのすべての操作で `true` に設定されています。クライアントはそのトランザクションをすべての操作にフローするため、アクションはクライアント トランザクションのスコープ内で発生します。</span><span class="sxs-lookup"><span data-stu-id="7840b-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="7840b-131">`TransactionAutoComplete` プロパティは、未処理の例外が発生しなかった場合にメソッドが実行中のトランザクションが自動的に完了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7840b-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="7840b-132">前述のように、このプロパティは加算操作および減算操作では `true` に設定されていますが、乗算操作および除算操作では `false` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7840b-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="7840b-133">加算操作と減算操作は、これらのアクションを自動的に完了し、除算操作は、`SetTransactionComplete` メソッドを明示的に呼び出すことによってアクションを完了します。乗算操作はアクションを完了せず、アクションを完了するために除算などを後で呼び出す必要があり、この呼び出しに依存しています。</span><span class="sxs-lookup"><span data-stu-id="7840b-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="7840b-134">属性サービスの実装は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7840b-134">The attributed service implementation is as follows:</span></span>  
  
```  
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 <span data-ttu-id="7840b-135">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7840b-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7840b-136">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7840b-136">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7840b-137">サービス操作要求のログ記録は、サービスのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7840b-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="7840b-138">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7840b-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="7840b-139">サービスは計算の現在高を保持することに加え、インスタンス (このサンプルでは 1 つのインスタンス) の作成を報告し、データベースのログに操作要求を記録します。</span><span class="sxs-lookup"><span data-stu-id="7840b-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="7840b-140">すべての要求はクライアント トランザクションをフローするため、トランザクションの完了に失敗した場合、すべてのデータベース操作がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="7840b-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="7840b-141">これについては、次のようないくつかの方法で示すことができます。</span><span class="sxs-lookup"><span data-stu-id="7840b-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="7840b-142">クライアントの `tx.Complete`() への呼び出しをコメント化して再実行します。これによってクライアントは、トランザクションを完了せずにトランザクション スコープを終了します。</span><span class="sxs-lookup"><span data-stu-id="7840b-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="7840b-143">除算サービス操作への呼び出しをコメント化します。これによって、乗算操作により初期化されたアクションの完了が回避され、したがって、クライアントのトランザクションの完了も最終的に失敗します。</span><span class="sxs-lookup"><span data-stu-id="7840b-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="7840b-144">未処理の例外を、クライアントのトランザクション スコープ内の任意の場所にスローします。これによってクライアントのトランザクションの完了が同様に回避されます。</span><span class="sxs-lookup"><span data-stu-id="7840b-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="7840b-145">これらの結果、スコープ内で実行される操作はコミットされず、データベースに保持されている行数はインクリメントしません。</span><span class="sxs-lookup"><span data-stu-id="7840b-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7840b-146">ビルド プロセスの一貫として、データベース ファイルが bin フォルダにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="7840b-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="7840b-147">このデータベース ファイルのコピーを調べ、Visual Studio プロジェクトに格納されているファイルではなく、ログに保存されている行を監視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7840b-148">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7840b-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7840b-149">SQL Server 2005 Express Edition または SQL Server 2005 がインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7840b-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="7840b-150">サービスの App.config ファイルでは、データベース接続文字列が `connectionString` に指定されているか、または `usingSql` に設定された appSettings `false` 値によりデータベースとの対話が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="7840b-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="7840b-151">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7840b-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7840b-152">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7840b-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="7840b-153">サンプルを別のコンピュータで実行する場合は、Microsoft 分散トランザクション コーディネータ (MSDTC) を構成してネットワーク トランザクション フローを有効にし、WsatConfig.exe ツールを使用して [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] トランザクション ネットワーク サポートを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="7840b-154">分散トランザクション コーディネータ (MSDTC) を構成してサンプルを別のコンピュータで実行できるようにするには</span><span class="sxs-lookup"><span data-stu-id="7840b-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="7840b-155">サービス コンピューターで、受信ネットワーク トランザクションを許可するように MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="7840b-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="7840b-156">**開始** メニューの "éˆú"**コントロール パネルの **、し**管理ツール**、し、**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="7840b-157">右クリック**マイ コンピューター**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="7840b-158">**MSDTC**  タブで、をクリックして**セキュリティ構成**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="7840b-159">確認**ネットワーク DTC アクセス**と**を許可する受信**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="7840b-160">をクリックして**はい**MS DTC サービスを再起動し、をクリックする**OK**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="7840b-161">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7840b-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="7840b-162">サービス コンピューターおよびクライアント コンピューターで、Windows ファイアウォールを構成します。例外アプリケーションのリストに、Microsoft 分散トランザクション コーディネーター (MSDTC) を追加します。</span><span class="sxs-lookup"><span data-stu-id="7840b-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="7840b-163">Windows ファイアウォール アプリケーションをコントロール パネルから実行します。</span><span class="sxs-lookup"><span data-stu-id="7840b-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="7840b-164">**例外** タブで、をクリックして**プログラムの追加**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="7840b-165">C:\WINDOWS\System32 フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="7840b-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="7840b-166">Msdtc.exe を選択し、クリックして**開く**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="7840b-167">をクリックして**ok**を閉じる、**プログラムの追加** ダイアログ ボックスをクリック**OK** Windows ファイアウォール アプレットを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7840b-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="7840b-168">クライアント コンピューターで、送信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="7840b-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="7840b-169">**開始** メニューの "éˆú"**コントロール パネルの **、し**管理ツール**、し、**コンポーネント サービス**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="7840b-170">右クリック**マイ コンピューター**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="7840b-171">**MSDTC**  タブで、をクリックして**セキュリティ構成**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="7840b-172">確認**ネットワーク DTC アクセス**と**送信を許可する**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="7840b-173">をクリックして**はい**MS DTC サービスを再起動し、をクリックする**OK**です。</span><span class="sxs-lookup"><span data-stu-id="7840b-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="7840b-174">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7840b-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7840b-175">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7840b-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7840b-176">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7840b-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7840b-177">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7840b-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7840b-178">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7840b-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="7840b-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="7840b-179">See Also</span></span>
