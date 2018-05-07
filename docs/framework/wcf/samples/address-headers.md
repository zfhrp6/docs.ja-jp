---
title: アドレス ヘッダー
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: c0e3807aadc18c7737f3a5e354135721cbfccf3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="address-headers"></a>アドレス ヘッダー
アドレス ヘッダーのサンプルでは、クライアントが Windows Communication Foundation (WCF) を使用してサービスに参照パラメーターを渡すことができる方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 WS-Addressing 仕様では、特定の Web サービスのエンドポイントのアドレスを指定するための方法として、エンドポイント参照の概念が定義されています。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、エンドポイント参照は `EndpointAddress` クラスを通じてモデル化されます。`EndpointAddress` は、`ServiceEndpoint` クラスの Address フィールドの型です。  
  
 エンドポイント参照モデルの一部では、各参照は、追加の識別情報を追加する複数の参照パラメータを伝達できます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、これらの参照パラメータは `AddressHeader` クラスのインスタンスとしてモデル化されます。  
  
 このサンプルでは、クライアントはクライアント エンドポイントの `EndpointAddress` に参照パラメータを追加します。 サービスはこの参照パラメータを検索し、その値を "Hello" サービス操作のロジックに使用します。  
  
## <a name="client"></a>クライアント  
 クライアントから参照パラメータを送信するには、`AddressHeader` の `EndpointAddress` に `ServiceEndpoint` を追加する必要があります。 `EndpointAddress` クラスは不変なので、EndpointAddress の変更は `EndpointAddressBuilder` クラスを通じて行う必要があります。 参照パラメータをメッセージの一部として送信するためにクライアントを初期化するコードを、次に示します。  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 このコードは、元の `EndpointAddressBuilder` を初期値として使用して `EndpointAddress` を作成します。 次に、新しく作成されたアドレス ヘッダーを追加します。つまり `CreateAddressHeadercreates` を呼び出して、特定の名前、名前空間、および値を持つヘッダーを作成します。 ここでの値は "John" です。 ヘッダーがビルダに追加されると、`ToEndpointAddress()` メソッドが (不変の) ビルダを (不変の) エンドポイント アドレスに変換し直し、これをクライアント エンドポイントの Address フィールドに再度割り当てます。  
  
 ここで、クライアントは `Console.WriteLine(client.Hello());` サービスを呼び出します。このサービスは、このアドレス パラメータの値を取得できます。結果として得られるクライアントの出力は次のとおりです。  
  
 `Hello, John`  
  
## <a name="server"></a>サーバー  
 サービス操作 `Hello()` の実装では、現在の `OperationContext` を使用して、入力メッセージのヘッダーの値を検査します。  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 このコードでは、入力メッセージのすべてのヘッダーを反復処理して、特定の名前を持つ参照パラメーターを検索します。 パラメーターが見つかると、そのパラメーター値を読み取って "id" 変数に格納します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>関連項目
