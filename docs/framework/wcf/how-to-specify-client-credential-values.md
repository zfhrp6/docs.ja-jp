---
title: "方法 : クライアントの資格情報の値を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd818a2342ff5b44e4e8ab1b237f7c657d3bf438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="fa022-102">方法 : クライアントの資格情報の値を指定する</span><span class="sxs-lookup"><span data-stu-id="fa022-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="fa022-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、サービスに対するクライアントの認証方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fa022-103">Using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="fa022-104">たとえば、証明書を使用してクライアントを認証するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="fa022-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="fa022-105">クライアント資格情報の種類を特定するには</span><span class="sxs-lookup"><span data-stu-id="fa022-105">To determine the client credential type</span></span>  
  
1.  <span data-ttu-id="fa022-106">サービスのメタデータ エンドポイントからメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="fa022-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="fa022-107">一般的に、メタデータは、選択したプログラミング言語 (既定は Visual C#) のクライアント コードおよび XML 構成ファイルという 2 つのファイルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="fa022-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="fa022-108">メタデータは、クライアント コードおよびクライアント構成を返す Svcutil.exe ツールを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="fa022-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="fa022-109">詳細については、次を参照してください。[メタデータを取得する](../../../docs/framework/wcf/feature-details/retrieving-metadata.md)と[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="fa022-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2.  <span data-ttu-id="fa022-110">XML 構成ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa022-110">Open the XML configuration file.</span></span> <span data-ttu-id="fa022-111">Svcutil.exe ツールを使用する場合、ファイルの既定の名前は、Output.config です。</span><span class="sxs-lookup"><span data-stu-id="fa022-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3.  <span data-ttu-id="fa022-112">検索、 **\<セキュリティ >**を持つ要素、**モード**属性 (**< セキュリティ モード =** `MessageOrTransport`  **>** 場所`MessageOrTransport`セキュリティ モードのいずれかに設定されています。</span><span class="sxs-lookup"><span data-stu-id="fa022-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4.  <span data-ttu-id="fa022-113">mode 値に一致する子要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="fa022-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="fa022-114">モードが に設定されている場合など、**メッセージ**、検索、 **\<メッセージ >**要素に含まれている、 **\<セキュリティ >**要素。</span><span class="sxs-lookup"><span data-stu-id="fa022-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5.  <span data-ttu-id="fa022-115">割り当てられた値に注意してください、 **clientCredentialType**属性。</span><span class="sxs-lookup"><span data-stu-id="fa022-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="fa022-116">実際の値は、使用されているモード (トランスポートまたはメッセージ) に依存します。</span><span class="sxs-lookup"><span data-stu-id="fa022-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="fa022-117">次の XML コードは、メッセージ セキュリティを使用し、クライアントの認証に証明書を要求するクライアントの構成を示します。</span><span class="sxs-lookup"><span data-stu-id="fa022-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="fa022-118">例: クライアント資格情報としての証明書による TCP トランスポート モード</span><span class="sxs-lookup"><span data-stu-id="fa022-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="fa022-119">この例では、セキュリティ モードを "Transport (トランスポート)" モードに設定し、クライアント資格情報の値を X.509 証明書に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa022-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="fa022-120">次の手順では、クライアントでクライアント資格情報の値をコードと構成を使用して設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fa022-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="fa022-121">これを使用している前提としています。、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をサービスからメタデータ (コードと構成) を返します。</span><span class="sxs-lookup"><span data-stu-id="fa022-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="fa022-122">[する方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="fa022-122"> [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="fa022-123">クライアントでクライアント資格情報の値をコードによって指定するには</span><span class="sxs-lookup"><span data-stu-id="fa022-123">To specify the client credential value on the client in code</span></span>  
  
1.  <span data-ttu-id="fa022-124">使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービスからコードと構成を生成します。</span><span class="sxs-lookup"><span data-stu-id="fa022-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2.  <span data-ttu-id="fa022-125">生成されたコードを使用して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa022-125">Create an instance of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client using the generated code.</span></span>  
  
3.  <span data-ttu-id="fa022-126">クライアント クラスで、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa022-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="fa022-127">この例では、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> メソッドを使用して、このプロパティを X.509 証明書に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa022-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="fa022-128"><xref:System.Security.Cryptography.X509Certificates.X509FindType> クラスの任意の列挙体を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fa022-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="fa022-129">ここでは、有効期限が切れて証明書が変更された場合に備えて、サブジェクト名を使用しています。</span><span class="sxs-lookup"><span data-stu-id="fa022-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="fa022-130">サブジェクト名を使用することにより、インフラストラクチャは証明書を再検索できます。</span><span class="sxs-lookup"><span data-stu-id="fa022-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="fa022-131">クライアントでクライアント資格情報の値を構成によって指定するには</span><span class="sxs-lookup"><span data-stu-id="fa022-131">To specify the client credential value on the client in configuration</span></span>  
  
1.  <span data-ttu-id="fa022-132">追加、 [\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素を[\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fa022-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2.  <span data-ttu-id="fa022-133">追加、 [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素を[\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fa022-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="fa022-134">`name` 属性 (必須) を適切な値に必ず設定してください。</span><span class="sxs-lookup"><span data-stu-id="fa022-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="fa022-135">追加、 [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)要素を[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fa022-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4.  <span data-ttu-id="fa022-136">次のコードに示すように、`storeLocation`、`storeName`、`x509FindType`、および `findValue` の各属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa022-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="fa022-137">証明書を参照してください[証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="fa022-137"> certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  <span data-ttu-id="fa022-138">クライアントを構成するときは、次のコードに示すように、`behaviorConfiguration` 要素の `<endpoint>` 属性を設定して動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa022-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="fa022-139">エンドポイント要素の子である、 [\<クライアント >](../../../docs/framework/configure-apps/file-schema/wcf/client.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fa022-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="fa022-140">また、`bindingConfiguration` 属性をクライアントのバインディングに設定することにより、バインディング構成の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa022-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="fa022-141">生成された構成ファイルを使用している場合は、バインディングの名前は自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="fa022-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="fa022-142">この例では、名前は `"tcpBindingWithCredential"` です。</span><span class="sxs-lookup"><span data-stu-id="fa022-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa022-143">参照</span><span class="sxs-lookup"><span data-stu-id="fa022-143">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="fa022-144">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="fa022-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="fa022-145">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="fa022-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="fa022-146">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="fa022-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="fa022-147">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="fa022-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="fa022-148">方法: クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="fa022-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="fa022-149">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="fa022-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [<span data-ttu-id="fa022-150">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="fa022-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [<span data-ttu-id="fa022-151">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="fa022-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [<span data-ttu-id="fa022-152">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="fa022-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [<span data-ttu-id="fa022-153">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="fa022-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [<span data-ttu-id="fa022-154">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="fa022-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [<span data-ttu-id="fa022-155">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="fa022-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
