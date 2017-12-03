---
title: "トランスポート : UDP 経由のカスタム トランザクションのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b17cb737533f1542b5f702097da4592df8e17eac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="98113-102">トランスポート : UDP 経由のカスタム トランザクションのサンプル</span><span class="sxs-lookup"><span data-stu-id="98113-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="98113-103">このサンプルがに基づいて、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルは、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)][トランスポート拡張](../../../../docs/framework/wcf/samples/transport-extensibility.md)です。</span><span class="sxs-lookup"><span data-stu-id="98113-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)][Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="98113-104">ここでは、カスタム トランザクション フローをサポートするように UDP トランスポートのサンプルを拡張し、<xref:System.ServiceModel.Channels.TransactionMessageProperty> プロパティの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98113-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="98113-105">UDP トランスポート サンプルのコードの変更</span><span class="sxs-lookup"><span data-stu-id="98113-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="98113-106">トランザクション フローを示すため、サンプルでは、`ICalculatorContract` のサービス コントラクトが `CalculatorService.Add()` のトランザクション スコープを要求するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="98113-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="98113-107">また、サンプルでは、別の `System.Guid` パラメータを `Add` 操作のコントラクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="98113-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="98113-108">このパラメータは、クライアント トランザクションの識別子をサービスに渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="98113-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);              
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="98113-109">[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルでは、UDP パケットを使用して、クライアントとサービス間でメッセージを渡します。</span><span class="sxs-lookup"><span data-stu-id="98113-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="98113-110">[トランスポート: カスタム トランスポートのサンプル](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md)同じメカニズムを使用してメッセージを転送するが、エンコードされたメッセージと一緒に UDP パケットが挿入されてトランザクションがフローされた場合。</span><span class="sxs-lookup"><span data-stu-id="98113-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="98113-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` は、メッセージ エンティティを使用して現在のトランザクションの反映トークンをマージし、それをバッファに配置する新しい機能を持つヘルパー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98113-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="98113-112">カスタム トランザクション フローのトランスポートの場合、クライアント実装では、トランザクション フローが必要なサービス操作と、この情報を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に渡す必要があるサービス操作を把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="98113-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="98113-113">また、ユーザー トランザクションをトランスポート層に転送するための機構もあります。</span><span class="sxs-lookup"><span data-stu-id="98113-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="98113-114">このサンプルでは、"[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージ インスペクタ" を使用して、この情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="98113-114">This sample uses "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message inspectors" to obtain this information.</span></span> <span data-ttu-id="98113-115">ここで実装されるクライアント メッセージ インスペクタは `TransactionFlowInspector` と呼ばれ、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="98113-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="98113-116">指定されたメッセージ アクションに対してトランザクションをフローする必要があるかどうかを判断します (これは `IsTxFlowRequiredForThisOperation()` で行われます)。</span><span class="sxs-lookup"><span data-stu-id="98113-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="98113-117">トランザクションをフローする必要がある場合、`TransactionFlowProperty` を使用して現在のアンビエント トランザクションをメッセージにアタッチします (これは `BeforeSendRequest()` で行われます)。</span><span class="sxs-lookup"><span data-stu-id="98113-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;             
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;              
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="98113-118">`TransactionFlowInspector` 自体は、カスタム動作 `TransactionFlowBehavior` を使用してフレームワークに渡されます。</span><span class="sxs-lookup"><span data-stu-id="98113-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="98113-119">上記の機構を使用して、ユーザー コードは、サービス操作を呼び出す前に `TransactionScope` を作成します。</span><span class="sxs-lookup"><span data-stu-id="98113-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="98113-120">メッセージ インスペクタは、トランザクションをサービス操作にフローする必要がある場合に、トランザクションがトランスポートに渡されるようにします。</span><span class="sxs-lookup"><span data-stu-id="98113-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());               
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }               
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="98113-121">クライアントから UDP パケットを受け取ると、サービスはこれを逆シリアル化して、メッセージとトランザクション (可能な場合) を抽出します。</span><span class="sxs-lookup"><span data-stu-id="98113-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="98113-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` は、`TransactionMessageBuffer.WriteTransactionMessageBuffer()` によって行われたシリアル化プロセスを元に戻すヘルパー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98113-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="98113-123">トランザクションがフローされた場合、トランザクションは `TransactionMessageProperty` のメッセージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="98113-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="98113-124">これにより、ディスパッチャはディスパッチ時にトランザクションを取得し、メッセージによってアドレス指定されたサービス操作を呼び出すときにそのトランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="98113-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="98113-125">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="98113-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="98113-126">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="98113-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="98113-127">同様に現在のサンプルを実行する必要があります、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="98113-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="98113-128">実行するには、UdpTestService.exe を使用してサービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="98113-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="98113-129">[!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] を実行している場合は、サービスをシステム特権で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98113-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="98113-130">これを行うで UdpTestService.exe を右クリックして[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] をクリック**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="98113-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="98113-131">これによって次の文字列が出力されます。</span><span class="sxs-lookup"><span data-stu-id="98113-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="98113-132">この時点で、UdpTestClient.exe を実行してクライアントを開始できます。</span><span class="sxs-lookup"><span data-stu-id="98113-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="98113-133">クライアントによって生成される出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98113-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="98113-134">サービスの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="98113-134">The service output is as follows.</span></span>  
  
    ```  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6.  <span data-ttu-id="98113-135">`The client transaction has flowed to the service` 操作の `clientTransactionId` パラメータで、クライアントによって送信されたトランザクション識別子がサービス トランザクションの識別子と一致する場合、サービス アプリケーションには、"`CalculatorService.Add()`" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98113-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="98113-136">クライアント トランザクションがサービスにフローされた場合にのみ、一致が取得されます。</span><span class="sxs-lookup"><span data-stu-id="98113-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="98113-137">構成を使用して公開されたエンドポイントに対してクライアント アプリケーションを実行するには、サービス側のアプリケーション ウィンドウで Enter キーを押して、テスト クライアントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="98113-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="98113-138">サービスには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98113-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="98113-139">サービスに対してクライアントを実行すると、前の出力と同様の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="98113-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="98113-140">Svcutil.exe を使用してクライアント コードと構成を再生成するには、サービス アプリケーションを開始し、次にサンプルのルート ディレクトリで次のように Svcutil.exe コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="98113-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="98113-141">Svcutil.exe を実行しても `sampleProfileUdpBinding` のバインディング拡張構成は生成されません。したがって、次のコードを手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98113-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>      
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="98113-142">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="98113-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98113-143">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="98113-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98113-144">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="98113-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98113-145">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="98113-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="98113-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="98113-146">See Also</span></span>  
 [<span data-ttu-id="98113-147">トランスポート: UDP</span><span class="sxs-lookup"><span data-stu-id="98113-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
