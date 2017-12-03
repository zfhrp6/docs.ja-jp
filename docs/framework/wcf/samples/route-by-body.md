---
title: "本文別のルーティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09e274bcbc1995dcd6b2c21e0114aa4a865f4129
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="route-by-body"></a>本文別のルーティング
このサンプルでは、任意の SOAP アクションでメッセージ オブジェクトを受け入れるサービスを実装する方法を示します。 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。 このサービスは、`Calculate` 要求パラメータを受け入れる 1 つの <xref:System.ServiceModel.Channels.Message> 操作を実装して、<xref:System.ServiceModel.Channels.Message> 応答を返します。  
  
 このサンプルでは、クライアントはコンソール アプリケーション (.exe) で、サービスは IIS によってホストされています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、本文の内容に基づくメッセージ ディスパッチを示します。 組み込みの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス モデルのメッセージ ディスパッチ メカニズムは、メッセージの Action に基づいています。 ただし既存の多くの Web サービスでは、すべての操作が Action="" で定義されています。 アクション情報に基づいてディスパッチ要求メッセージを保持する WSDL を基準として、サービスを構築することはできません。 このサンプルでは、WSDL に基づくサービス コントラクトを示します (WSDL はこのサンプルに含まれる Service.wsdl 内に格納されています)。 サービス コントラクトはで使用されるように、電卓[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。 ただし、`[OperationContract]` は、すべての操作に対して `Action=""` を指定します。  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 コントラクトが指定されている場合、サービスはカスタムのディスパッチ動作 `DispatchByBodyBehavior` に対して、複数の操作間でメッセージをディスパッチするように要求します。 このディスパッチ動作を初期化、`DispatchByBodyElementOperationSelector`それぞれのラッパー要素の QName をキーとした操作名のテーブルでのカスタム操作セレクター。 `DispatchByBodyElementOperationSelector` は本文の最初の子の開始タグを参照し、前述のテーブルを使用して操作を選択します。  
  
 クライアントを使用して、サービスによってエクスポートされた WSDL から自動生成されたプロキシを使用して[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 すべての操作のアクションが空であっても、クライアント コードには影響ありません。ただし、自動生成されたプロキシ内の Action パラメータは例外です。  
  
 クライアント コードは、複数の計算を実行します。 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a>関連項目
