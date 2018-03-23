---
title: '方法 : チャネルのセキュリティ資格情報を指定する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: ''
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: e2aedb06ec694f6c7dfb12b70ab919ae23eed17e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-specify-channel-security-credentials"></a>方法 : チャネルのセキュリティ資格情報を指定する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス モニカーを使用すると、COM アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを呼び出すことができます。 ほとんどの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスで、クライアントは認証と承認のための資格情報の指定が要求されます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントから呼び出す場合、この資格情報をマネージ コードまたはアプリケーション構成ファイルに指定できます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを COM アプリケーションから呼び出す場合、<xref:System.ServiceModel.ComIntegration.IChannelCredentials> インターフェイスを使用して資格情報を指定できます。 ここでは、<xref:System.ServiceModel.ComIntegration.IChannelCredentials> インターフェイスを使用して資格情報を指定するさまざまな方法を説明します。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> は IDispatch ベースのインターフェイスです。Visual Studio 環境で IntelliSense 機能を取得することはできません。  
  
 この記事の内容を使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]で定義されたサービス、[メッセージ セキュリティ サンプル](../../../../docs/framework/wcf/samples/message-security-sample.md)です。  
  
### <a name="to-specify-a-client-certificate"></a>クライアント証明書を指定するには  
  
1.  メッセージ セキュリティのディレクトリの Setup.bat ファイルを実行し、必要なテスト証明書を作成してインストールします。  
  
2.  メッセージ セキュリティのプロジェクトを開きます。  
  
3.  追加`[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]`を`ICalculator`インターフェイス定義です。  
  
4.  追加`bindingNamespace=``http://Microsoft.ServiceModel.Samples`サービス用の App.config 内のエンドポイント タグにします。  
  
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
  
     Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> または <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> を <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> の代わりに使用して、クライアント証明書を設定することもできます。  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  この呼び出しを機能させるには、クライアントが実行されているコンピューターでクライアント証明書を信頼する必要があります。  
  
> [!NOTE]
>  モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。 このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
### <a name="to-specify-user-name-and-password"></a>ユーザー名とパスワードを指定するには  
  
1.  `wsHttpBinding` を使用するよう App.config ファイルを変更します。 これは、ユーザー名とパスワードの検証に必要です。  
  
  
  
2.  `clientCredentialType` を UserName に設定します。  
  
  
  
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
    >  この例のサービス モニカーに指定されたバインディングは、WSHttpBinding_ICalculator に変更されました。 また、<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> の呼び出しにも有効なユーザー名とパスワードを指定する必要があります。  
  
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
  
1.  発行トークンは、フェデレーション セキュリティを使用するアプリケーションのみが使用します。 フェデレーション セキュリティの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)と[フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)です。  
  
     <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> メソッドを呼び出す方法を次の Visual Basic コード例に示します。  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     このメソッドのパラメーターの詳細については、<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)  
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [方法 : フェデレーション クライアントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [メッセージのセキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
