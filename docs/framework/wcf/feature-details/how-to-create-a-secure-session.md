---
title: "方法 : セキュリティで保護されたセッションを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: cd4f91ef5389dd4b8ecb63c1148d3a86918f2d10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="229c7-102">方法 : セキュリティで保護されたセッションを作成する</span><span class="sxs-lookup"><span data-stu-id="229c7-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="229c7-103">例外を除いて、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)のシステム指定のバインディング、バインディング[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]メッセージ セキュリティが有効になっているセキュリティで保護されたセッションを自動的に使用します。</span><span class="sxs-lookup"><span data-stu-id="229c7-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="229c7-104">既定では、セキュリティで保護されたセッションは、再利用される Web サーバーで存続します。</span><span class="sxs-lookup"><span data-stu-id="229c7-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="229c7-105">セキュリティで保護されたセッションが確立されると、クライアントとサービスが、セキュリティで保護されたセッションに関連付けられているキーをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="229c7-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="229c7-106">メッセージを交換するときは、キャッシュされたキーの識別子のみが交換されます。</span><span class="sxs-lookup"><span data-stu-id="229c7-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="229c7-107">Web サーバーが再利用される場合は、Web サーバーが識別子のキャッシュされたキーを取得できないようにキャッシュも再利用されます。</span><span class="sxs-lookup"><span data-stu-id="229c7-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="229c7-108">これが発生した場合、例外がクライアントにスローされます。</span><span class="sxs-lookup"><span data-stu-id="229c7-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="229c7-109">ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用するセキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。</span><span class="sxs-lookup"><span data-stu-id="229c7-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="229c7-110">セキュリティで保護されたセッションでステートフルな SCT を使用して参照してください[する方法: セキュリティで保護されたセッションのセキュリティ コンテキスト トークンを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="229c7-110"> using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="229c7-111">サービスが、システム提供のバインディングの 1 つを使用して、セキュリティで保護されたセッションを使用するように指定するには</span><span class="sxs-lookup"><span data-stu-id="229c7-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="229c7-112">メッセージ セキュリティをサポートするシステム提供のバインディングを使用するようにサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="229c7-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="229c7-113">例外を除いて、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)メッセージ セキュリティを使用するシステム提供のバインディングが構成されている場合、バインディング、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]自動的にセキュリティで保護されたセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="229c7-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically uses secure sessions.</span></span> <span data-ttu-id="229c7-114">次の表は、メッセージ セキュリティをサポートするシステム提供のバインディングを示し、そのバインディングでメッセージ セキュリティが既定のセキュリティ機構であるかどうかを示しています。</span><span class="sxs-lookup"><span data-stu-id="229c7-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="229c7-115">システム提供のバインディング</span><span class="sxs-lookup"><span data-stu-id="229c7-115">System-provided binding</span></span>|<span data-ttu-id="229c7-116">構成要素</span><span class="sxs-lookup"><span data-stu-id="229c7-116">Configuration element</span></span>|<span data-ttu-id="229c7-117">既定でメッセージ セキュリティが有効</span><span class="sxs-lookup"><span data-stu-id="229c7-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="229c7-118">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="229c7-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="229c7-119">×</span><span class="sxs-lookup"><span data-stu-id="229c7-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="229c7-120">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="229c7-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="229c7-121">[はい]</span><span class="sxs-lookup"><span data-stu-id="229c7-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="229c7-122">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="229c7-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="229c7-123">[はい]</span><span class="sxs-lookup"><span data-stu-id="229c7-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="229c7-124">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="229c7-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="229c7-125">[はい]</span><span class="sxs-lookup"><span data-stu-id="229c7-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="229c7-126">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="229c7-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="229c7-127">×</span><span class="sxs-lookup"><span data-stu-id="229c7-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="229c7-128">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="229c7-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="229c7-129">×</span><span class="sxs-lookup"><span data-stu-id="229c7-129">No</span></span>|  
  
     <span data-ttu-id="229c7-130">次のコード例は、という名前のバインディングを指定する構成を使用して`wsHttpBinding_Calculator`を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションです。</span><span class="sxs-lookup"><span data-stu-id="229c7-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="229c7-131">次のコード例を指定する、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションをセキュリティで保護を使用する、`secureCalculator`サービス。</span><span class="sxs-lookup"><span data-stu-id="229c7-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="229c7-132">セキュリティで保護されたセッションを無効にできる、 [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を設定して、`establishSecurityContext`属性を`false`です。</span><span class="sxs-lookup"><span data-stu-id="229c7-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="229c7-133">他のシステム提供のバインディングについては、カスタム バインドを作成することでのみ、セキュリティで保護されたセッションを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="229c7-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="229c7-134">カスタム バインディングを使用して、サービスでセキュリティで保護されたセッションが使用されるように指定するには</span><span class="sxs-lookup"><span data-stu-id="229c7-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="229c7-135">セキュリティで保護されたセッションで SOAP メッセージが保護されるように指定したカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="229c7-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="229c7-136">カスタム バインドの作成を参照してください[する方法: システム指定のバインディングをカスタマイズ](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)です。</span><span class="sxs-lookup"><span data-stu-id="229c7-136"> creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="229c7-137">次のコード例で使用されている構成では、セキュリティで保護されたセッションを使用して SOAP メッセージを保護するカスタム バインドを指定しています。</span><span class="sxs-lookup"><span data-stu-id="229c7-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="229c7-138">セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 認証モードを使用する、カスタム バインディングを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="229c7-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="229c7-139">参照</span><span class="sxs-lookup"><span data-stu-id="229c7-139">See Also</span></span>  
 [<span data-ttu-id="229c7-140">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="229c7-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
