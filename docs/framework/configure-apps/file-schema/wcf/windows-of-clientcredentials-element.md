---
title: "&lt;clientCredentials&gt; 要素の &lt;windows&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6687f93be26dedcb34f08770708c072742fdd4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="dff77-102">&lt;clientCredentials&gt; 要素の &lt;windows&gt;</span><span class="sxs-lookup"><span data-stu-id="dff77-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="dff77-103">クライアントを表すために使用される Windows 資格情報の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="dff77-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="dff77-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dff77-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dff77-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="dff77-105">\<behaviors></span></span>  
<span data-ttu-id="dff77-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dff77-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="dff77-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="dff77-107">\<behavior></span></span>  
<span data-ttu-id="dff77-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="dff77-108">\<clientCredentials></span></span>  
<span data-ttu-id="dff77-109">\<windows ></span><span class="sxs-lookup"><span data-stu-id="dff77-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff77-110">構文</span><span class="sxs-lookup"><span data-stu-id="dff77-110">Syntax</span></span>  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dff77-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dff77-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dff77-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dff77-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dff77-113">属性</span><span class="sxs-lookup"><span data-stu-id="dff77-113">Attributes</span></span>  
  
|<span data-ttu-id="dff77-114">属性</span><span class="sxs-lookup"><span data-stu-id="dff77-114">Attribute</span></span>|<span data-ttu-id="dff77-115">説明</span><span class="sxs-lookup"><span data-stu-id="dff77-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="dff77-116">クライアントがサーバーと通信する偽装設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="dff77-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="dff77-117">クライアントが選択する偽装モードは、サーバーでは適用されません。</span><span class="sxs-lookup"><span data-stu-id="dff77-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="dff77-118">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="dff77-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dff77-119">識別します。 サーバーは、id およびクライアントの権限を取得できますが、クライアントを偽装することはできません。</span><span class="sxs-lookup"><span data-stu-id="dff77-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="dff77-120">偽装: サーバーは、ローカル システム上のクライアントのセキュリティ コンテキストを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="dff77-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="dff77-121">委任: サーバーはリモート システム上のクライアントのセキュリティ コンテキストを偽装することができます。</span><span class="sxs-lookup"><span data-stu-id="dff77-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="dff77-122">-Anonymous: サーバーことはできませんの権限を借用またはクライアントを識別します。</span><span class="sxs-lookup"><span data-stu-id="dff77-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="dff77-123">-None: 偽装レベルが割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="dff77-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="dff77-124">既定値は Identification です。</span><span class="sxs-lookup"><span data-stu-id="dff77-124">The default is Identification.</span></span> <span data-ttu-id="dff77-125">この属性は <xref:System.Security.Principal.TokenImpersonationLevel> 型です。</span><span class="sxs-lookup"><span data-stu-id="dff77-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="dff77-126">このプロパティを `true` に設定すると、Kerberos 認証を利用できない場合、NTLM 認証にダウングレードできます。</span><span class="sxs-lookup"><span data-stu-id="dff77-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="dff77-127">このプロパティを `false` に設定すると、NTLM が使用されている場合、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] はベスト エフォートで例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="dff77-127">Setting this property to `false` causes [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="dff77-128">ただし、このプロパティを `false` に設定しても、ネットワーク経由で NTLM 資格情報が送信されなくなるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="dff77-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dff77-129">子要素</span><span class="sxs-lookup"><span data-stu-id="dff77-129">Child Elements</span></span>  
 <span data-ttu-id="dff77-130">なし。</span><span class="sxs-lookup"><span data-stu-id="dff77-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dff77-131">親要素</span><span class="sxs-lookup"><span data-stu-id="dff77-131">Parent Elements</span></span>  
  
|<span data-ttu-id="dff77-132">要素</span><span class="sxs-lookup"><span data-stu-id="dff77-132">Element</span></span>|<span data-ttu-id="dff77-133">説明</span><span class="sxs-lookup"><span data-stu-id="dff77-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dff77-134">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="dff77-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="dff77-135">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="dff77-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dff77-136">参照</span><span class="sxs-lookup"><span data-stu-id="dff77-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="dff77-137">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="dff77-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="dff77-138">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="dff77-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="dff77-139">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="dff77-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
