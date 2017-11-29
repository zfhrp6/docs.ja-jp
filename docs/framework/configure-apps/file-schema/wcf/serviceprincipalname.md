---
title: "&lt;サービス プリンシパル名&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e472c7fcfd57341074489a75f7954be38291523b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="133ff-102">&lt;サービス プリンシパル名&gt;</span><span class="sxs-lookup"><span data-stu-id="133ff-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="133ff-103">サービスの ID をサービス プリンシパル名 (SPN) により指定します。</span><span class="sxs-lookup"><span data-stu-id="133ff-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="133ff-104">SPN を設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="133ff-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="133ff-105">\<id ></span><span class="sxs-lookup"><span data-stu-id="133ff-105">\<identity></span></span>  
<span data-ttu-id="133ff-106">\<サービス プリンシパル名 ></span><span class="sxs-lookup"><span data-stu-id="133ff-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="133ff-107">構文</span><span class="sxs-lookup"><span data-stu-id="133ff-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="133ff-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="133ff-108">Attributes and Elements</span></span>  
 <span data-ttu-id="133ff-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="133ff-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="133ff-110">属性</span><span class="sxs-lookup"><span data-stu-id="133ff-110">Attributes</span></span>  
  
|<span data-ttu-id="133ff-111">属性</span><span class="sxs-lookup"><span data-stu-id="133ff-111">Attribute</span></span>|<span data-ttu-id="133ff-112">説明</span><span class="sxs-lookup"><span data-stu-id="133ff-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="133ff-113">value</span><span class="sxs-lookup"><span data-stu-id="133ff-113">value</span></span>|<span data-ttu-id="133ff-114">クライアントがサービスのインスタンスを一意に識別する名前です。</span><span class="sxs-lookup"><span data-stu-id="133ff-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="133ff-115">フォレストの複数のコンピューターに 1 つのサービスの複数のインスタンスをインストールする場合、各インスタンスには独自の SPN が必要です。</span><span class="sxs-lookup"><span data-stu-id="133ff-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="133ff-116">クライアントが認証に使用できる複数の名前がある場合は、指定したサービス インスタンスに複数の SPN を設定できます。</span><span class="sxs-lookup"><span data-stu-id="133ff-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="133ff-117">子要素</span><span class="sxs-lookup"><span data-stu-id="133ff-117">Child Elements</span></span>  
 <span data-ttu-id="133ff-118">なし。</span><span class="sxs-lookup"><span data-stu-id="133ff-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="133ff-119">親要素</span><span class="sxs-lookup"><span data-stu-id="133ff-119">Parent Elements</span></span>  
  
|<span data-ttu-id="133ff-120">要素</span><span class="sxs-lookup"><span data-stu-id="133ff-120">Element</span></span>|<span data-ttu-id="133ff-121">説明</span><span class="sxs-lookup"><span data-stu-id="133ff-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="133ff-122">\<id ></span><span class="sxs-lookup"><span data-stu-id="133ff-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="133ff-123">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="133ff-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="133ff-124">コメント</span><span class="sxs-lookup"><span data-stu-id="133ff-124">Remarks</span></span>  
 <span data-ttu-id="133ff-125">この ID を持つエンドポイントに接続するセキュリティで保護された [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアントは、エンドポイントの SSPI 認証を実行するときに SPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="133ff-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133ff-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="133ff-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="133ff-127">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="133ff-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="133ff-128">\<id ></span><span class="sxs-lookup"><span data-stu-id="133ff-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
