---
title: "方法 : トランスポート セキュリティとメッセージ資格情報を使用する"
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
helpviewer_keywords: TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 70575732e7840d243373fd1512f788c776f17ceb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="b9042-102">方法 : トランスポート セキュリティとメッセージ資格情報を使用する</span><span class="sxs-lookup"><span data-stu-id="b9042-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="b9042-103">トランスポート資格情報とメッセージ資格情報の両方を使用してサービスをセキュリティで保護する場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、トランスポート セキュリティ モードとメッセージ セキュリティ モードの両方が最適に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9042-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="b9042-104">つまり、トランスポート層セキュリティでは整合性と機密性が提供され、メッセージ層セキュリティでは、厳密なトランスポート セキュリティ機構では実現できないさまざまな資格情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b9042-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="b9042-105">ここでは、<xref:System.ServiceModel.WSHttpBinding> バインディングと <xref:System.ServiceModel.NetTcpBinding> バインディングを使用して、メッセージ資格情報付きトランスポートを実装するための基本手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b9042-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b9042-106">セキュリティ モードを設定するには、表示[する方法: セキュリティ モードを設定](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9042-106"> setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="b9042-107">セキュリティ モードを `TransportWithMessageCredential` に設定した場合、トランスポート レベルのセキュリティを提供する実際の機構はトランスポートによって決まります。</span><span class="sxs-lookup"><span data-stu-id="b9042-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="b9042-108">この機構は、HTTP の場合は SSL (Secure Sockets Layer) over HTTP (HTTPS)、TCP の場合は SSL over TCP または Windows です。</span><span class="sxs-lookup"><span data-stu-id="b9042-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="b9042-109">トランスポートが HTTP (<xref:System.ServiceModel.WSHttpBinding> を使用) の場合は、トランスポート レベルのセキュリティが SSL over HTTP によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="b9042-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="b9042-110">この場合、このトピックで後述するように、ポートにバインドされた SSL 証明書を使用してサービスをホストするコンピューターを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9042-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="b9042-111">トランスポートが TCP (<xref:System.ServiceModel.NetTcpBinding> を使用) の場合、既定では、Windows セキュリティ または SSL over TCP によってトランスポート レベルのセキュリティが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b9042-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="b9042-112">SSL over TCP を使用する場合は、このトピックで後述するように、<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> メソッドを使用して証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9042-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="b9042-113">WSHttpBinding と証明書を使用してトランスポート セキュリティを提供するには (コードを使用する場合)</span><span class="sxs-lookup"><span data-stu-id="b9042-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="b9042-114">HttpCfg.exe ツールを使用して、コンピューターの任意のポートに SSL 証明書をバインドします。</span><span class="sxs-lookup"><span data-stu-id="b9042-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b9042-115">[する方法: SSL 証明書でポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9042-115"> [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="b9042-116"><xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.WSHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="b9042-117"><xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="b9042-118">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [資格情報の種類を選択すると](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md))。次のコードでは、<xref:System.ServiceModel.MessageCredentialType.Certificate> 値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b9042-118">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="b9042-119">適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9042-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="b9042-120">このアドレスでは、"HTTPS" スキームを使用し、コンピューターの実際の名前と SSL 証明書のバインド先のポート番号を含める必要があります </span><span class="sxs-lookup"><span data-stu-id="b9042-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="b9042-121">(または、構成で基本アドレスを設定できます。)</span><span class="sxs-lookup"><span data-stu-id="b9042-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="b9042-122"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9042-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="b9042-123"><xref:System.ServiceModel.ServiceHost> のインスタンスを作成し、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b9042-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="b9042-124">NetTcpBinding と証明書を使用してトランスポート セキュリティを提供するには (コードを使用する場合)</span><span class="sxs-lookup"><span data-stu-id="b9042-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="b9042-125"><xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="b9042-126"><xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="b9042-127">次のコードでは、<xref:System.ServiceModel.MessageCredentialType.Certificate> 値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b9042-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="b9042-128">適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9042-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="b9042-129">アドレスには "net.tcp" スキーマを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9042-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="b9042-130">(または、構成で基本アドレスを設定できます。)</span><span class="sxs-lookup"><span data-stu-id="b9042-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="b9042-131"><xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9042-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="b9042-132"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> メソッドを使用して、サービスに X.509 資格情報を明示的に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="b9042-133"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9042-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="b9042-134">次のコードに示すように、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9042-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="b9042-135">NetTcpBinding と Windows を使用してトランスポート セキュリティを提供するには (コードを使用する場合)</span><span class="sxs-lookup"><span data-stu-id="b9042-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="b9042-136"><xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="b9042-137">トランスポート セキュリティが Windows を使用するように、<xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> を <xref:System.ServiceModel.TcpClientCredentialType.Windows> に設定します </span><span class="sxs-lookup"><span data-stu-id="b9042-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="b9042-138">(これは、既定の設定です)。</span><span class="sxs-lookup"><span data-stu-id="b9042-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="b9042-139"><xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="b9042-140">次のコードでは、<xref:System.ServiceModel.MessageCredentialType.Certificate> 値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b9042-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="b9042-141">適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9042-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="b9042-142">アドレスには "net.tcp" スキーマを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9042-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="b9042-143">(または、構成で基本アドレスを設定できます。)</span><span class="sxs-lookup"><span data-stu-id="b9042-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="b9042-144"><xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9042-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="b9042-145"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> メソッドを使用して、サービスに X.509 資格情報を明示的に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="b9042-146"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9042-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="b9042-147">次のコードに示すように、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9042-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="b9042-148">構成の使用</span><span class="sxs-lookup"><span data-stu-id="b9042-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="b9042-149">WSHttpBinding を使用するには</span><span class="sxs-lookup"><span data-stu-id="b9042-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="b9042-150">ポートにバインドされた SSL 証明書を使用してコンピューターを構成します。</span><span class="sxs-lookup"><span data-stu-id="b9042-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="b9042-151">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [する方法: SSL 証明書でポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md))。</span><span class="sxs-lookup"><span data-stu-id="b9042-151">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="b9042-152">設定する必要はありません、<`transport`> この構成要素の値。</span><span class="sxs-lookup"><span data-stu-id="b9042-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="b9042-153">メッセージ レベルのセキュリティのクライアント資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="b9042-154">次の例のセット、`clientCredentialType`の属性、<`message`> 要素を`UserName`です。</span><span class="sxs-lookup"><span data-stu-id="b9042-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="b9042-155">NetTcpBinding と証明書を使用してトランスポート セキュリティを提供するには</span><span class="sxs-lookup"><span data-stu-id="b9042-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="b9042-156">SSL over TCP の場合、`<behaviors>` 要素内で証明書を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9042-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="b9042-157">既定のストアの場所 (ローカル コンピューターの個人ストア) にある証明書を、発行者で指定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9042-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="b9042-158">追加、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)バインディング セクションに</span><span class="sxs-lookup"><span data-stu-id="b9042-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="b9042-159">バインド要素を追加して、`name` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="b9042-160">追加する <`security`> 要素、およびセット、`mode`属性を`TransportWithMessageCredential`です。</span><span class="sxs-lookup"><span data-stu-id="b9042-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="b9042-161">追加する <`message>`要素、およびセット、`clientCredentialType`属性を適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="b9042-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="b9042-162">NetTcpBinding と Windows を使用してトランスポート セキュリティを提供するには</span><span class="sxs-lookup"><span data-stu-id="b9042-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="b9042-163">追加、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)すると、バインディング セクション</span><span class="sxs-lookup"><span data-stu-id="b9042-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="b9042-164">追加する <`binding`> 要素、`name`属性を適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="b9042-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="b9042-165">追加する <`security`> 要素、およびセット、`mode`属性を`TransportWithMessageCredential`です。</span><span class="sxs-lookup"><span data-stu-id="b9042-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="b9042-166">追加する <`transport`> 要素、`clientCredentialType`属性を`Windows`です。</span><span class="sxs-lookup"><span data-stu-id="b9042-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="b9042-167">追加する <`message`> 要素、`clientCredentialType`属性を適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="b9042-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="b9042-168">次のコードは、値を証明書に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9042-168">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b9042-169">参照</span><span class="sxs-lookup"><span data-stu-id="b9042-169">See Also</span></span>  
 [<span data-ttu-id="b9042-170">方法: セキュリティ モードを設定する</span><span class="sxs-lookup"><span data-stu-id="b9042-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [<span data-ttu-id="b9042-171">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b9042-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="b9042-172">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b9042-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
