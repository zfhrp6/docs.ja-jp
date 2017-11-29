---
title: "方法 : ユーザー名とパスワードで認証する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73ef3c3f4f4aeb9295cedbbf56635454869b3f4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>方法 : ユーザー名とパスワードで認証する
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスが Windows ドメイン ユーザー名とパスワードを使用してクライアントを認証できるようにする方法を示します。 自己ホスト型 WCF サービスが稼働していることを前提としています。 基本的な自己ホスト型 WCF サービスは、「作成の例については[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)です。 このトピックでは、サービスがコードで構成されているものとします。 構成ファイルを使用して同様のサービスを構成する例を参照してくださいを表示したい場合[メッセージ セキュリティ ユーザー名](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Windows ドメイン ユーザー名とパスワードを使用してそのクライアントを認証するサービスを構成する、<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 設定とその`Security.Mode`プロパティを`Message`です。 また、ユーザー名とパスワードをクライアントからサービスに送信するときに X.509 証明書を指定する必要があります。この証明書は、ユーザー名とパスワードの暗号化に使用されます。  
  
 クライアント側では、ユーザーにユーザー名とパスワードの入力を求め、WCF クライアント プロキシでユーザーの資格情報を指定する必要があります。  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Windows ドメイン ユーザー名とパスワードを使用して認証するように WCF サービスを構成するには  
  
1.  インスタンスを作成、<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> へのバインドのセキュリティ モードを設定`SecurityMode.Message`、設定、`ClientCredentialType`へのバインドの`MessageCredentialType.UserName`、しのように、サービス ホストに構成されたバインディングを使用してサービス エンドポイントを追加次のコード。  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  ネットワーク経由で送信されるユーザー名とパスワードの情報を暗号化するために使用するサーバー証明書を指定します。 次のコードは、上記のコードの直後に追加します。 次の例から、setup.bat ファイルによって作成される証明書を使用して、[メッセージ セキュリティ ユーザー名](../../../../docs/framework/wcf/samples/message-security-user-name.md)サンプル。  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     独自の証明書を使用する場合は、その証明書を参照するようにコードを変更します。 作成して、証明書の使用の詳細については、次を参照してください。[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。 証明書がローカル コンピューターの信頼されたユーザー証明書ストア内に存在することを確認します。 Mmc.exe を実行し、選択してこれを行う、**ファイル**、**スナップインの追加/削除しています.**メニュー項目。 **を追加または削除スナップイン**ダイアログで、選択、**証明書スナップイン** をクリック**追加**です。 証明書スナップイン ダイアログで選択**コンピューター アカウント**です。 既定では、「メッセージ セキュリティ ユーザー名」のサンプルから生成された証明書は個人/証明書フォルダーに配置されます。  [MMC のウィンドウ内の列に発行] には、"localhost"として表示されます。 ドラッグ アンド ドロップした証明書を**信頼されたユーザー**フォルダーです。 これにより、WCF は、認証の実行時に、証明書を信頼された証明書として処理することができます。  
  
### <a name="to-call-the-service-passing-username-and-password"></a>ユーザー名とパスワードを渡すサービスを呼び出すには  
  
1.  クライアント アプリケーションは、ユーザー名とパスワードの入力をユーザーに求める必要があります。 次のコードでは、ユーザー名とパスワードの入力をユーザーに求めます。  
  
    > [!WARNING]
    >  このコードは、入力中のパスワードが表示されるため、運用環境では使用しないでください。  
  
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
  
2.  次のコードに示すように、クライアントの資格情報を指定して、クライアント プロキシのインスタンスを作成します。  
  
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
  
## <a name="see-also"></a>関連項目  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [基本認証でのトランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [分散アプリケーションのセキュリティ](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
