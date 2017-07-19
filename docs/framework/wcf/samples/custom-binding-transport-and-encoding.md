---
title: "カスタム バインディングのトランスポートとエンコード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# カスタム バインディングのトランスポートとエンコード
カスタム バインディングは、個々のバインディング要素の順序付きリストとして定義されます。このサンプルでは、さまざまなトランスポートとメッセージ エンコーディング要素を使用してカスタム バインディングを構成する方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは「[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)」に基づいており、HTTP、TCP、NamedPipe の各トランスポートがカスタム バインディングでサポートされるように、3 つのエンドポイントの構成が変更されています。クライアント構成も同様に変更され、クライアント コードは 3 つのエンドポイントそれぞれと通信するように変更されています。  
  
 このサンプルでは、特定のトランスポートとメッセージ エンコーディング要素をサポートするカスタム バインディングを構成する方法を示します。これを行うには、`binding` 要素のトランスポートとメッセージ エンコーディングを構成します。カスタム バインディングを定義するうえで、バインディング要素の順序は重要です。各バインディング要素は、チャネル スタック内のレイヤを表すからです \(「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください\)。このサンプルでは、テキスト エンコーディングによる HTTP トランスポート、テキスト エンコーディングによる TCP トランスポート、およびバイナリ エンコーディングによる NamedPipe トランスポートの 3 つのカスタム バインディングを構成します。  
  
 サービス構成では、次のようにカスタム バインディングが定義されます。  
  
```  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。クライアントは、3 つのエンドポイントのそれぞれと通信します。最初に HTTP、次に TCP、最後に NamedPipe にアクセスします。どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
 `namedPipeTransport` バインディングは、複数のコンピュータ間の操作をサポートしません。同じコンピュータの通信だけに使用されます。したがって、このサンプルを複数コンピュータのシナリオで実行する場合は、クライアント コード ファイル内の次の行をコメント化してください。  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
>  Svcutil.exe を使用してこのサンプルの構成を再生成した場合は、クライアント コードに一致するように、クライアント構成内のエンドポイント名を変更してください。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版、C\+\+ 版、または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## 参照