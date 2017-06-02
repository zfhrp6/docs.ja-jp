---
title: "セキュリティ検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: 35
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 35
---
# セキュリティ検証
このサンプルでは、サービスが特定の条件を満たしていることを確認するカスタム動作を使用して、コンピューター上のサービスを検証する方法を示します。このサンプルでは、サービス上の各エンドポイントをスキャンし、セキュリティ保護されたバインディング要素が含まれているかどうかを確認するカスタム動作を使用して、サービスを検証します。このサンプルは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## エンドポイント検証のカスタム動作  
 <xref:System.ServiceModel.Description.IServiceBehavior> インターフェイスに含まれる `Validate` メソッドにユーザー コードを追加することによって、サービスまたはエンドポイントにカスタム動作を与え、ユーザー定義のアクションを実行することができます。次のコードを使用すると、サービスに含まれる各エンドポイントをループし、バインディング コレクションからセキュリティ保護されたバインディングが検索されます。  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 次のコードを Web.config ファイルに追加すると、サービスで識別される `serviceValidate` 動作の拡張が追加されます。  
  
```  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 動作の拡張がサービスに追加されると、`endpointValidate` の動作を Web.config ファイルの動作リストに追加でき、さらにはサービスに追加できるようになります。  
  
```  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 動作とその拡張が Web.config ファイルに追加されると、動作は個別のサービスに適用されます。一方で Machine.config ファイルに追加された場合は、動作はコンピューター上でアクティブなすべてのサービスに適用されます。  
  
> [!NOTE]
>  動作をすべてのサービスに追加する場合、Machine.config ファイルの変更を行う前に、このファイルのバックアップを推奨するメッセージが表示されます。  
  
 ここで、このサンプルの client\\bin ディレクトリに用意されたクライアントを実行します。例外が発生して、"要求されたサービス、'http:\/\/localhost\/servicemodelsamples\/service.svc' を起動できませんでした。" というメッセージが表示されます。これは予期される例外です。エンドポイント検証の動作により、エンドポイントがセキュリティで保護されていないと見なされ、サービスが開始されないためです。さらにこの動作によって、エンドポイントがセキュリティ保護されていないという内部例外がスローされ、システム イベント ビューアで "WebHost" カテゴリの "System.ServiceModel 4.0.0.0" ソースの下にメッセージが書き込まれます。さらにこのサンプルでは、サービスのトレースを有効にできます。これによって、サービス トレース ビューア ツールを使用してサービス トレースの結果を開き、エンドポイント検証の動作からスローされた例外を表示することができます。  
  
#### エンドポイント検証エラーの例外メッセージをイベント ビューアーで表示するには  
  
1.  **\[スタート\]** メニューをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
2.  「`eventvwr`」と入力して **\[OK\]** をクリックします。  
  
3.  \[イベント ビューアー\] ウィンドウの **\[アプリケーション\]** をクリックします。  
  
4.  **\[アプリケーション\]** ウィンドウで、"WebHost" カテゴリの下に最近追加された "System.ServiceModel 4.0.0.0" イベントをダブルクリックし、セキュリティ保護されていないエンドポイントのメッセージを表示します。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)