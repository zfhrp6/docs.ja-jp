---
title: "&lt;netMsmqBinding&gt; の &lt;message&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdef94f5ee570d7ce93544950a5a290d3eb534f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="cec3a-102">&lt;netMsmqBinding&gt; の &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="cec3a-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="cec3a-103">この `netMsmqBinding` バインディングでの SOAP メッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="cec3a-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cec3a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cec3a-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cec3a-105">\<bindings></span></span>  
<span data-ttu-id="cec3a-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="cec3a-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="cec3a-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cec3a-107">\<binding></span></span>  
<span data-ttu-id="cec3a-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="cec3a-108">\<security></span></span>  
<span data-ttu-id="cec3a-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="cec3a-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec3a-110">構文</span><span class="sxs-lookup"><span data-stu-id="cec3a-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cec3a-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cec3a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cec3a-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cec3a-113">属性</span><span class="sxs-lookup"><span data-stu-id="cec3a-113">Attributes</span></span>  
  
|<span data-ttu-id="cec3a-114">属性</span><span class="sxs-lookup"><span data-stu-id="cec3a-114">Attribute</span></span>|<span data-ttu-id="cec3a-115">説明</span><span class="sxs-lookup"><span data-stu-id="cec3a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cec3a-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="cec3a-116">algorithmSuite</span></span>|<span data-ttu-id="cec3a-117">MSMQ トランスポートを介して送信されるメッセージにメッセージ ベースのセキュリティを実現するために使用されるメッセージの暗号化およびキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="cec3a-118">既定値は `Aes256` です。</span><span class="sxs-lookup"><span data-stu-id="cec3a-118">The default value is `Aes256`.</span></span> <span data-ttu-id="cec3a-119">この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="cec3a-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="cec3a-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="cec3a-120">clientCredentialType</span></span>|<span data-ttu-id="cec3a-121">MSMQ トランスポートで送信されるメッセージに対してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="cec3a-122">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="cec3a-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cec3a-123">-なし: これにより、匿名クライアントとの対話をサービスします。</span><span class="sxs-lookup"><span data-stu-id="cec3a-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="cec3a-124">サービスとクライアントはいずれも資格情報を要求しません。</span><span class="sxs-lookup"><span data-stu-id="cec3a-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="cec3a-125">Windows 資格情報の認証されたコンテキスト下にある SOAP 交換これにより、Windows: です。</span><span class="sxs-lookup"><span data-stu-id="cec3a-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="cec3a-126">これは、常に Kerberos ベースの認証を実行します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="cec3a-127">-ユーザー名。 これにより、サービスを必要とする UserName 資格情報を使用してクライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="cec3a-128">ここでは資格情報を使用して指定する必要があります、`clientCredentials`動作**注意:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]はパスワードを送信するには、ダイジェスト認証または派生キーのパスワードを使用して、メッセージ セキュリティのようなキーの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cec3a-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="cec3a-129">したがって、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、UserName 資格情報を使用する場合に交換が強制的に保護されるようにします。</span><span class="sxs-lookup"><span data-stu-id="cec3a-129">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="cec3a-130">このモードは、サービス証明書が、`clientCredential` 動作および `serviceCertificate` を使用してクライアント側で指定されることを要求します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="cec3a-131">証明書: これにより、サービスを必要とする証明書を使用してクライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="cec3a-132">この場合のクライアント資格情報は、`clientCredentials` 動作を使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec3a-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="cec3a-133">この場合のサービス資格情報は、`clientCredentials` を指定して `serviceCertificate` 動作を使用することで、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec3a-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="cec3a-134">-CardSpace: これにより、サービスを必要とする、CardSpace を使用してクライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="cec3a-135">`serviceCertiifcate` は、`clientCredential` 動作で提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec3a-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="cec3a-136">既定値は `Windows` です。</span><span class="sxs-lookup"><span data-stu-id="cec3a-136">The default value is `Windows`.</span></span> <span data-ttu-id="cec3a-137">この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="cec3a-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cec3a-138">子要素</span><span class="sxs-lookup"><span data-stu-id="cec3a-138">Child Elements</span></span>  
 <span data-ttu-id="cec3a-139">なし</span><span class="sxs-lookup"><span data-stu-id="cec3a-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cec3a-140">親要素</span><span class="sxs-lookup"><span data-stu-id="cec3a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="cec3a-141">要素</span><span class="sxs-lookup"><span data-stu-id="cec3a-141">Element</span></span>|<span data-ttu-id="cec3a-142">説明</span><span class="sxs-lookup"><span data-stu-id="cec3a-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cec3a-143">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="cec3a-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="cec3a-144">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cec3a-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cec3a-145">参照</span><span class="sxs-lookup"><span data-stu-id="cec3a-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="cec3a-146">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="cec3a-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="cec3a-147">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="cec3a-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cec3a-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="cec3a-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cec3a-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="cec3a-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cec3a-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="cec3a-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cec3a-151">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cec3a-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
