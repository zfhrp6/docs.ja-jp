---
title: "方法 : ユーザー名とパスワードで認証する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "認証 [WCF], ユーザー名とパスワード"
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 方法 : ユーザー名とパスワードで認証する
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスが Windows ドメイン ユーザー名とパスワードを使用してクライアントを認証できるようにする方法を示します。自己ホスト型 WCF サービスが稼働していることを前提としています。基本的な自己ホスト型 WCF サービスを作成する例については、「[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。このトピックでは、サービスがコードで構成されているものとします。構成ファイルを使用して同様のサービスを構成する例については、「[メッセージ セキュリティ ユーザー名](../../../../docs/framework/wcf/samples/message-security-user-name.md)」を参照してください。  
  
 Windows ドメイン ユーザー名とパスワードを使用してクライアントを認証するようにサービスを構成するには、<xref:System.ServiceModel.WSHttpBinding> を使用し、その `Security.Mode` プロパティを `Message` に設定します。また、ユーザー名とパスワードをクライアントからサービスに送信するときにそれらを暗号化するために使用する X.509 証明書を指定する必要があります。  
  
 クライアント側では、ユーザー名とパスワードをユーザーにたずね、WCF クライアント プロキシでユーザーの資格情報を指定する必要があります。  
  
### Windows ドメイン ユーザー名とパスワードを使用して認証するように WCF サービスを構成するには  
  
1.  次のコードに示すように、<xref:System.ServiceModel.WSHttpBinding> のインスタンスを作成し、バインディングのセキュリティ モードを `SecurityMode.Message` に設定した後、バインディングの `ClientCredentialType` を `MessageCredentialType.UserName` に設定し、構成されたバインディングを使用するサービス エンドポイントをサービス ホストに追加します。  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  ネットワーク経由で送信されるユーザー名とパスワードの情報を暗号化するために使用するサーバー証明書を指定します。このコードは、上記のコードの直後に追加します。次の例では、「[メッセージ セキュリティ ユーザー名](../../../../docs/framework/wcf/samples/message-security-user-name.md)」のサンプルの setup.bat ファイルによって作成された証明書を使用します。  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     独自の証明書を使用する場合は、その証明書を参照するようにコードを変更します。証明書の作成と使用の詳細については、「[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。証明書がローカル マシンの信頼されたユーザーの証明書ストア内に存在することを確認します。これを行うには、mmc.exe を実行し、**\[ファイル\]**、**\[スナップインの追加と削除\]** メニュー項目を順にクリックします。**\[スナップインの追加と削除\]** ダイアログ ボックスで、**\[証明書スナップイン\]** を選択し、**\[追加\]** をクリックします。\[証明書スナップイン\] ダイアログ ボックスで、**\[コンピューター アカウント\]** を選択します。既定では、メッセージ セキュリティ ユーザー名のサンプルから生成された証明書は個人\/証明書フォルダーに配置されます。これは、MMC ウィンドウの \[発行先\] 列に "localhost" として表示されます。**\[信頼されたユーザー\]** フォルダーに証明書をドラッグ アンド ドロップします。これにより、認証を実行するときに、WCF は証明書を信頼された証明書として処理することができます。  
  
### ユーザー名とパスワードを渡すサービスを呼び出すには  
  
1.  クライアント アプリケーションは、ユーザー名とパスワードをユーザーにたずねる必要があります。次のコードでは、ユーザー名とパスワードをユーザーにたずねます。  
  
    > [!WARNING]
    >  このコードは、パスワードが入力中に表示されるため、運用環境では使用しないでください。  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
  
    ```  
  
2.  次のコードのように、クライアントの資格情報を指定して、クライアント プロキシのインスタンスを作成します。  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## 参照  
 <xref:System.ServiceModel.WsHttpBinding>   
 <xref:System.ServiceModel.WSHttpSecurity>   
 <xref:System.ServiceModel.SecurityMode>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>   
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>   
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>   
 [基本認証でのトランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)   
 [分散アプリケーションのセキュリティ](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)   
 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)