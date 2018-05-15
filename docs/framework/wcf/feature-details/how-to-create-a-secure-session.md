---
title: '方法 : セキュリティで保護されたセッションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ce351a87e70b09a2f68654af817e28fa3145d79d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="82c68-102">方法 : セキュリティで保護されたセッションを作成する</span><span class="sxs-lookup"><span data-stu-id="82c68-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="82c68-103">例外を除いて、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)バインド、システム指定のバインディングで Windows Communication Foundation (WCF) に自動的にセッションを使用するセキュリティで保護されたメッセージ セキュリティが有効な場合です。</span><span class="sxs-lookup"><span data-stu-id="82c68-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="82c68-104">既定では、セキュリティで保護されたセッションは、再利用される Web サーバーで存続します。</span><span class="sxs-lookup"><span data-stu-id="82c68-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="82c68-105">セキュリティで保護されたセッションが確立されると、クライアントとサービスが、セキュリティで保護されたセッションに関連付けられているキーをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="82c68-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="82c68-106">メッセージを交換するときは、キャッシュされたキーの識別子のみが交換されます。</span><span class="sxs-lookup"><span data-stu-id="82c68-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="82c68-107">Web サーバーが再利用される場合は、Web サーバーが識別子のキャッシュされたキーを取得できないようにキャッシュも再利用されます。</span><span class="sxs-lookup"><span data-stu-id="82c68-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="82c68-108">これが発生した場合、例外がクライアントにスローされます。</span><span class="sxs-lookup"><span data-stu-id="82c68-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="82c68-109">ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用するセキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。</span><span class="sxs-lookup"><span data-stu-id="82c68-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="82c68-110">詳細については、セキュリティで保護されたセッションでステートフルな SCT を使用して、次を参照してください。[する方法: セキュリティで保護されたセッションのセキュリティ コンテキスト トークンを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="82c68-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="82c68-111">サービスが、システム提供のバインディングの 1 つを使用して、セキュリティで保護されたセッションを使用するように指定するには</span><span class="sxs-lookup"><span data-stu-id="82c68-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="82c68-112">メッセージ セキュリティをサポートするシステム提供のバインディングを使用するようにサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="82c68-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="82c68-113">例外を除いて、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)セキュリティで保護されたセッションを使用して WCF メッセージ セキュリティを自動的に使用するシステム提供のバインディングが構成されている場合、バインドします。</span><span class="sxs-lookup"><span data-stu-id="82c68-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="82c68-114">次の表は、メッセージ セキュリティをサポートするシステム提供のバインディングを示し、そのバインディングでメッセージ セキュリティが既定のセキュリティ機構であるかどうかを示しています。</span><span class="sxs-lookup"><span data-stu-id="82c68-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="82c68-115">システム提供のバインディング</span><span class="sxs-lookup"><span data-stu-id="82c68-115">System-provided binding</span></span>|<span data-ttu-id="82c68-116">構成要素</span><span class="sxs-lookup"><span data-stu-id="82c68-116">Configuration element</span></span>|<span data-ttu-id="82c68-117">既定でメッセージ セキュリティが有効</span><span class="sxs-lookup"><span data-stu-id="82c68-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="82c68-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="82c68-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="82c68-119">×</span><span class="sxs-lookup"><span data-stu-id="82c68-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="82c68-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="82c68-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="82c68-121">[はい]</span><span class="sxs-lookup"><span data-stu-id="82c68-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="82c68-122">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="82c68-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="82c68-123">[はい]</span><span class="sxs-lookup"><span data-stu-id="82c68-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="82c68-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="82c68-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="82c68-125">[はい]</span><span class="sxs-lookup"><span data-stu-id="82c68-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="82c68-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="82c68-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="82c68-127">×</span><span class="sxs-lookup"><span data-stu-id="82c68-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="82c68-128">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="82c68-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="82c68-129">×</span><span class="sxs-lookup"><span data-stu-id="82c68-129">No</span></span>|  
  
     <span data-ttu-id="82c68-130">次のコード例は、という名前のバインディングを指定する構成を使用して`wsHttpBinding_Calculator`を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションです。</span><span class="sxs-lookup"><span data-stu-id="82c68-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="82c68-131">次のコード例を指定する、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションをセキュリティで保護を使用する、`secureCalculator`サービス。</span><span class="sxs-lookup"><span data-stu-id="82c68-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="82c68-132">セキュリティで保護されたセッションを無効にできる、 [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を設定して、`establishSecurityContext`属性を`false`です。</span><span class="sxs-lookup"><span data-stu-id="82c68-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="82c68-133">他のシステム提供のバインディングについては、カスタム バインドを作成することでのみ、セキュリティで保護されたセッションを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="82c68-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="82c68-134">カスタム バインディングを使用して、サービスでセキュリティで保護されたセッションが使用されるように指定するには</span><span class="sxs-lookup"><span data-stu-id="82c68-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="82c68-135">セキュリティで保護されたセッションで SOAP メッセージが保護されるように指定したカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="82c68-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="82c68-136">カスタム バインドの作成の詳細については、次を参照してください。[する方法: システム指定のバインディングをカスタマイズ](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)です。</span><span class="sxs-lookup"><span data-stu-id="82c68-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="82c68-137">次のコード例で使用されている構成では、セキュリティで保護されたセッションを使用して SOAP メッセージを保護するカスタム バインドを指定しています。</span><span class="sxs-lookup"><span data-stu-id="82c68-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="82c68-138">セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 認証モードを使用する、カスタム バインディングを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="82c68-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="82c68-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="82c68-139">See Also</span></span>  
 [<span data-ttu-id="82c68-140">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="82c68-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
