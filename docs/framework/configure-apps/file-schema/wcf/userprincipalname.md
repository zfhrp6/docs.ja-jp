---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23e2599920c0ef0ea35569ec9b0b16b0f8735f1a
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="3d73d-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="3d73d-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="3d73d-103">クライアントで認証するサービスのユーザー プリンシパル名 (UPN) を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d73d-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="3d73d-104">UPN を設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d73d-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="3d73d-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="3d73d-105">\<identity></span></span>  
<span data-ttu-id="3d73d-106">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="3d73d-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d73d-107">構文</span><span class="sxs-lookup"><span data-stu-id="3d73d-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d73d-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3d73d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3d73d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3d73d-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d73d-110">属性</span><span class="sxs-lookup"><span data-stu-id="3d73d-110">Attributes</span></span>  
  
|<span data-ttu-id="3d73d-111">属性</span><span class="sxs-lookup"><span data-stu-id="3d73d-111">Attribute</span></span>|<span data-ttu-id="3d73d-112">説明</span><span class="sxs-lookup"><span data-stu-id="3d73d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d73d-113">value</span><span class="sxs-lookup"><span data-stu-id="3d73d-113">value</span></span>|<span data-ttu-id="3d73d-114">ユーザー アカウント名 (ユーザー ログイン名と呼ばれることもある) と、ユーザー アカウントの検索範囲のドメインを識別するドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="3d73d-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="3d73d-115">これは、Windows ドメインにログオンするための標準的使用方法です。</span><span class="sxs-lookup"><span data-stu-id="3d73d-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="3d73d-116">形式:someone@example.comです (の場合、電子メール アドレスなど)。</span><span class="sxs-lookup"><span data-stu-id="3d73d-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d73d-117">子要素</span><span class="sxs-lookup"><span data-stu-id="3d73d-117">Child Elements</span></span>  
 <span data-ttu-id="3d73d-118">なし。</span><span class="sxs-lookup"><span data-stu-id="3d73d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d73d-119">親要素</span><span class="sxs-lookup"><span data-stu-id="3d73d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3d73d-120">要素</span><span class="sxs-lookup"><span data-stu-id="3d73d-120">Element</span></span>|<span data-ttu-id="3d73d-121">説明</span><span class="sxs-lookup"><span data-stu-id="3d73d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d73d-122">\<identity></span><span class="sxs-lookup"><span data-stu-id="3d73d-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3d73d-123">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d73d-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d73d-124">コメント</span><span class="sxs-lookup"><span data-stu-id="3d73d-124">Remarks</span></span>  
 <span data-ttu-id="3d73d-125">この ID を持つエンドポイントに接続する、セキュリティで保護された [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアントは、エンドポイントの SSPI 認証を実行するときに UPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d73d-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d73d-126">例</span><span class="sxs-lookup"><span data-stu-id="3d73d-126">Example</span></span>  
 <span data-ttu-id="3d73d-127">次の構成コードは、クライアントで認証するサービスの UPN を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d73d-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d73d-128">参照</span><span class="sxs-lookup"><span data-stu-id="3d73d-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="3d73d-129">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="3d73d-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="3d73d-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="3d73d-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
