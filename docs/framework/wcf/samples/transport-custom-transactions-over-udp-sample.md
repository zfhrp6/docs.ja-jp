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
ms.workload: dotnet
ms.openlocfilehash: 7e26d0c25879b3b1b6ed873543f051de989ddd92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a>トランスポート : UDP 経由のカスタム トランザクションのサンプル
このサンプルがに基づいて、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルは、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)][トランスポート拡張](../../../../docs/framework/wcf/samples/transport-extensibility.md)です。 ここでは、カスタム トランザクション フローをサポートするように UDP トランスポートのサンプルを拡張し、<xref:System.ServiceModel.Channels.TransactionMessageProperty> プロパティの使用方法について説明します。  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>UDP トランスポート サンプルのコードの変更  
 トランザクション フローを示すため、サンプルでは、`ICalculatorContract` のサービス コントラクトが `CalculatorService.Add()` のトランザクション スコープを要求するように変更されています。 また、サンプルでは、別の `System.Guid` パラメータを `Add` 操作のコントラクトに追加します。 このパラメータは、クライアント トランザクションの識別子をサービスに渡すために使用されます。  
  
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
  
 [トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルでは、UDP パケットを使用して、クライアントとサービス間でメッセージを渡します。 [トランスポート: カスタム トランスポートのサンプル](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md)同じメカニズムを使用してメッセージを転送するが、エンコードされたメッセージと一緒に UDP パケットが挿入されてトランザクションがフローされた場合。  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer` は、メッセージ エンティティを使用して現在のトランザクションの反映トークンをマージし、それをバッファに配置する新しい機能を持つヘルパー メソッドです。  
  
 カスタム トランザクション フローのトランスポートの場合、クライアント実装では、トランザクション フローが必要なサービス操作と、この情報を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に渡す必要があるサービス操作を把握している必要があります。 また、ユーザー トランザクションをトランスポート層に転送するための機構もあります。 このサンプルでは、"[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージ インスペクタ" を使用して、この情報を取得します。 ここで実装されるクライアント メッセージ インスペクタは `TransactionFlowInspector` と呼ばれ、次のタスクを実行します。  
  
-   指定されたメッセージ アクションに対してトランザクションをフローする必要があるかどうかを判断します (これは `IsTxFlowRequiredForThisOperation()` で行われます)。  
  
-   トランザクションをフローする必要がある場合、`TransactionFlowProperty` を使用して現在のアンビエント トランザクションをメッセージにアタッチします (これは `BeforeSendRequest()` で行われます)。  
  
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
  
 `TransactionFlowInspector` 自体は、カスタム動作 `TransactionFlowBehavior` を使用してフレームワークに渡されます。  
  
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
  
 上記の機構を使用して、ユーザー コードは、サービス操作を呼び出す前に `TransactionScope` を作成します。 メッセージ インスペクタは、トランザクションをサービス操作にフローする必要がある場合に、トランザクションがトランスポートに渡されるようにします。  
  
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
  
 クライアントから UDP パケットを受け取ると、サービスはこれを逆シリアル化して、メッセージとトランザクション (可能な場合) を抽出します。  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()` は、`TransactionMessageBuffer.WriteTransactionMessageBuffer()` によって行われたシリアル化プロセスを元に戻すヘルパー メソッドです。  
  
 トランザクションがフローされた場合、トランザクションは `TransactionMessageProperty` のメッセージに追加されます。  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 これにより、ディスパッチャはディスパッチ時にトランザクションを取得し、メッセージによってアドレス指定されたサービス操作を呼び出すときにそのトランザクションを使用します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
2.  同様に現在のサンプルを実行する必要があります、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。 実行するには、UdpTestService.exe を使用してサービスを開始します。 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] を実行している場合は、サービスをシステム特権で開始する必要があります。 これを行うで UdpTestService.exe を右クリックして[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] をクリック**管理者として実行**です。  
  
3.  これによって次の文字列が出力されます。  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  この時点で、UdpTestClient.exe を実行してクライアントを開始できます。 クライアントによって生成される出力を次に示します。  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  サービスの出力は、次のようになります。  
  
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
  
6.  `The client transaction has flowed to the service` 操作の `clientTransactionId` パラメータで、クライアントによって送信されたトランザクション識別子がサービス トランザクションの識別子と一致する場合、サービス アプリケーションには、"`CalculatorService.Add()`" というメッセージが表示されます。 クライアント トランザクションがサービスにフローされた場合にのみ、一致が取得されます。  
  
7.  構成を使用して公開されたエンドポイントに対してクライアント アプリケーションを実行するには、サービス側のアプリケーション ウィンドウで Enter キーを押して、テスト クライアントを再実行します。 サービスには、次の出力が表示されます。  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  サービスに対してクライアントを実行すると、前の出力と同様の出力が生成されます。  
  
9. Svcutil.exe を使用してクライアント コードと構成を再生成するには、サービス アプリケーションを開始し、次にサンプルのルート ディレクトリで次のように Svcutil.exe コマンドを実行します。  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Svcutil.exe を実行しても `sampleProfileUdpBinding` のバインディング拡張構成は生成されません。したがって、次のコードを手動で追加する必要があります。  
  
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
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>参照  
 [トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
