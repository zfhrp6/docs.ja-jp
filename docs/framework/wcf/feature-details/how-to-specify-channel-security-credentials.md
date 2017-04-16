---
title: "方法 : チャネルのセキュリティ資格情報を指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# 方法 : チャネルのセキュリティ資格情報を指定する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス モニカーを使用すると、COM アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを呼び出すことができます。 ほとんどの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスで、クライアントは認証と承認のための資格情報の指定が要求されます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントから呼び出す場合、この資格情報をマネージ コードまたはアプリケーション構成ファイルに指定できます。 呼び出すときに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス、COM アプリケーションから使用して、 <xref:System.ServiceModel.ComIntegration.IChannelCredentials>インターフェイス資格情報を指定します。 このトピックを使用して資格情報を指定するさまざまな方法を示しますが、 <xref:System.ServiceModel.ComIntegration.IChannelCredentials>インターフェイスです。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> IDispatch ベースのインターフェイスは、Visual Studio 環境で IntelliSense 機能は得られません。  
  
 この記事を使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]で定義されたサービス、[メッセージ セキュリティ サンプル](../../../../docs/framework/wcf/samples/message-security-sample.md)します。  
  
### <a name="to-specify-a-client-certificate"></a>クライアント証明書を指定するには  
  
1.  メッセージ セキュリティのディレクトリの Setup.bat ファイルを実行し、必要なテスト証明書を作成してインストールします。  
  
2.  メッセージ セキュリティのプロジェクトを開きます。  
  
3.  追加`[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]`に、`ICalculator`インターフェイス定義です。  
  
4.  追加`bindingNamespace=``http://Microsoft.ServiceModel.Samples`サービスの App.config 内のエンドポイント タグにします。  
  
5.  メッセージ セキュリティ サンプルをビルドし、Service.exe を実行します。 Internet Explorer を使用してサービスの URI (http://localhost:8000/ServiceModelSamples/Service) を参照し、サービスが動作していることを確認します。  
  
6.  Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。 フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7.  Visual Basic アプリケーションを実行し、結果を確認します。  
  
     Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>または<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>の代わりに使用することもできます<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29>クライアント資格情報を設定します。  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  この呼び出しを機能させるには、クライアントが実行されているコンピューターでクライアント証明書を信頼する必要があります。  
  
> [!NOTE]
>  モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。 このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
### <a name="to-specify-user-name-and-password"></a>ユーザー名とパスワードを指定するには  
  
1.  `wsHttpBinding` を使用するよう App.config ファイルを変更します。 これは、ユーザー名とパスワードの検証に必要です。  
  
  
  
2.  
          `clientCredentialType` を UserName に設定します。  
  
  
  
3.  Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。 フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  Visual Basic アプリケーションを実行し、結果を確認します。 Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。  
  
    > [!NOTE]
    >  この例のサービス モニカーに指定されたバインディングは、WSHttpBinding_ICalculator に変更されました。 なお、有効なユーザー名とパスワードへの呼び出しで指定する必要があります<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>します。  
  
### <a name="to-specify-windows-credentials"></a>Windows 資格情報を指定するには  
  
1.  サービスの App.config ファイルで、`clientCredentialType` を Windows に設定します。  
  
  
  
2.  Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。 フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  Visual Basic アプリケーションを実行し、結果を確認します。 Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。  
  
    > [!NOTE]
    >  "ドメイン"、"ユーザー ID"、"パスワード" を有効な値に置き換える必要があります。  
  
### <a name="to-specify-an-issue-token"></a>発行トークンを指定するには  
  
1.  発行トークンは、フェデレーション セキュリティを使用するアプリケーションのみが使用します。 フェデレーション セキュリティの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)と[フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)します。  
  
     次の Visual Basic のコード例を呼び出す方法を示しています、 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>メソッド。  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     このメソッドのパラメーターの詳細については、次を参照してください。 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>します。  
  
## <a name="see-also"></a>関連項目  
 [フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)   
 [方法: フェデレーション サービスで資格情報を構成します。](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [方法: フェデレーション クライアントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [メッセージ セキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)   
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)