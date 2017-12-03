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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31e05709465e429445a2ebdafae719c24d316c8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="0c12a-102">方法 : ユーザー名とパスワードで認証する</span><span class="sxs-lookup"><span data-stu-id="0c12a-102">How to: Authenticate with a User Name and Password</span></span>
<span data-ttu-id="0c12a-103">ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスが Windows ドメイン ユーザー名とパスワードを使用してクライアントを認証できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0c12a-103">This topic demonstrates how to enable a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="0c12a-104">自己ホスト型 WCF サービスが稼働していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="0c12a-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="0c12a-105">基本的な自己ホスト型 WCF サービスは、「作成の例については[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c12a-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="0c12a-106">このトピックでは、サービスがコードで構成されているものとします。</span><span class="sxs-lookup"><span data-stu-id="0c12a-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="0c12a-107">構成ファイルを使用して同様のサービスを構成する例を参照してくださいを表示したい場合[メッセージ セキュリティ ユーザー名](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="0c12a-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="0c12a-108">Windows ドメイン ユーザー名とパスワードを使用してそのクライアントを認証するサービスを構成する、<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 設定とその`Security.Mode`プロパティを`Message`です。</span><span class="sxs-lookup"><span data-stu-id="0c12a-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="0c12a-109">また、ユーザー名とパスワードをクライアントからサービスに送信するときに X.509 証明書を指定する必要があります。この証明書は、ユーザー名とパスワードの暗号化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0c12a-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="0c12a-110">クライアント側では、ユーザーにユーザー名とパスワードの入力を求め、WCF クライアント プロキシでユーザーの資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c12a-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="0c12a-111">Windows ドメイン ユーザー名とパスワードを使用して認証するように WCF サービスを構成するには</span><span class="sxs-lookup"><span data-stu-id="0c12a-111">To configure a WCF service to authenticate using Windows domain username and password.</span></span>  
  
1.  <span data-ttu-id="0c12a-112">インスタンスを作成、<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> へのバインドのセキュリティ モードを設定`SecurityMode.Message`、設定、`ClientCredentialType`へのバインドの`MessageCredentialType.UserName`、しのように、サービス ホストに構成されたバインディングを使用してサービス エンドポイントを追加次のコード。</span><span class="sxs-lookup"><span data-stu-id="0c12a-112">Create an instance of the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, set the security mode of the binding to `SecurityMode.Message`, set the `ClientCredentialType` of the binding to `MessageCredentialType.UserName`, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="0c12a-113">ネットワーク経由で送信されるユーザー名とパスワードの情報を暗号化するために使用するサーバー証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c12a-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="0c12a-114">次のコードは、上記のコードの直後に追加します。</span><span class="sxs-lookup"><span data-stu-id="0c12a-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="0c12a-115">次の例から、setup.bat ファイルによって作成される証明書を使用して、[メッセージ セキュリティ ユーザー名](../../../../docs/framework/wcf/samples/message-security-user-name.md)サンプル。</span><span class="sxs-lookup"><span data-stu-id="0c12a-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="0c12a-116">独自の証明書を使用する場合は、その証明書を参照するようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="0c12a-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="0c12a-117">作成して、証明書の使用の詳細については、次を参照してください。[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c12a-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="0c12a-118">証明書がローカル コンピューターの信頼されたユーザー証明書ストア内に存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c12a-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="0c12a-119">Mmc.exe を実行し、選択してこれを行う、**ファイル**、**スナップインの追加/削除しています.**メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="0c12a-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="0c12a-120">**を追加または削除スナップイン**ダイアログで、選択、**証明書スナップイン** をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="0c12a-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="0c12a-121">証明書スナップイン ダイアログで選択**コンピューター アカウント**です。</span><span class="sxs-lookup"><span data-stu-id="0c12a-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="0c12a-122">既定では、「メッセージ セキュリティ ユーザー名」のサンプルから生成された証明書は個人/証明書フォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="0c12a-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="0c12a-123">[MMC のウィンドウ内の列に発行] には、"localhost"として表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c12a-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="0c12a-124">ドラッグ アンド ドロップした証明書を**信頼されたユーザー**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="0c12a-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="0c12a-125">これにより、WCF は、認証の実行時に、証明書を信頼された証明書として処理することができます。</span><span class="sxs-lookup"><span data-stu-id="0c12a-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
### <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="0c12a-126">ユーザー名とパスワードを渡すサービスを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="0c12a-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="0c12a-127">クライアント アプリケーションは、ユーザー名とパスワードの入力をユーザーに求める必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c12a-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="0c12a-128">次のコードでは、ユーザー名とパスワードの入力をユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="0c12a-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="0c12a-129">このコードは、入力中のパスワードが表示されるため、運用環境では使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="0c12a-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
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
  
2.  <span data-ttu-id="0c12a-130">次のコードに示すように、クライアントの資格情報を指定して、クライアント プロキシのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c12a-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c12a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c12a-131">See Also</span></span>  
 <span data-ttu-id="0c12a-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="0c12a-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [<span data-ttu-id="0c12a-133">基本認証でのトランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0c12a-133">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [<span data-ttu-id="0c12a-134">分散アプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="0c12a-134">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="0c12a-135">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0c12a-135">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
