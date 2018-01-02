---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34bfaeb563bd4979bf29a5e45a60730eb38700b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="43edc-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="43edc-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="43edc-103">クライアントで認証するサービスのユーザー プリンシパル名 (UPN) を指定します。</span><span class="sxs-lookup"><span data-stu-id="43edc-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="43edc-104">UPN を設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="43edc-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="43edc-105">\<id ></span><span class="sxs-lookup"><span data-stu-id="43edc-105">\<identity></span></span>  
<span data-ttu-id="43edc-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="43edc-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43edc-107">構文</span><span class="sxs-lookup"><span data-stu-id="43edc-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43edc-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="43edc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43edc-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="43edc-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43edc-110">属性</span><span class="sxs-lookup"><span data-stu-id="43edc-110">Attributes</span></span>  
  
|<span data-ttu-id="43edc-111">属性</span><span class="sxs-lookup"><span data-stu-id="43edc-111">Attribute</span></span>|<span data-ttu-id="43edc-112">説明</span><span class="sxs-lookup"><span data-stu-id="43edc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43edc-113">value</span><span class="sxs-lookup"><span data-stu-id="43edc-113">value</span></span>|<span data-ttu-id="43edc-114">ユーザー アカウント名 (ユーザー ログイン名と呼ばれることもある) と、ユーザー アカウントの検索範囲のドメインを識別するドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="43edc-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="43edc-115">これは、Windows ドメインにログオンするための標準的使用方法です。</span><span class="sxs-lookup"><span data-stu-id="43edc-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="43edc-116">形式: someone@example.com (電子メール アドレス) です。</span><span class="sxs-lookup"><span data-stu-id="43edc-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43edc-117">子要素</span><span class="sxs-lookup"><span data-stu-id="43edc-117">Child Elements</span></span>  
 <span data-ttu-id="43edc-118">なし。</span><span class="sxs-lookup"><span data-stu-id="43edc-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43edc-119">親要素</span><span class="sxs-lookup"><span data-stu-id="43edc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="43edc-120">要素</span><span class="sxs-lookup"><span data-stu-id="43edc-120">Element</span></span>|<span data-ttu-id="43edc-121">説明</span><span class="sxs-lookup"><span data-stu-id="43edc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43edc-122">\<id ></span><span class="sxs-lookup"><span data-stu-id="43edc-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="43edc-123">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="43edc-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43edc-124">コメント</span><span class="sxs-lookup"><span data-stu-id="43edc-124">Remarks</span></span>  
 <span data-ttu-id="43edc-125">この ID を持つエンドポイントに接続する、セキュリティで保護された [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアントは、エンドポイントの SSPI 認証を実行するときに UPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="43edc-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43edc-126">例</span><span class="sxs-lookup"><span data-stu-id="43edc-126">Example</span></span>  
 <span data-ttu-id="43edc-127">次の構成コードは、クライアントで認証するサービスの UPN を指定します。</span><span class="sxs-lookup"><span data-stu-id="43edc-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43edc-128">参照</span><span class="sxs-lookup"><span data-stu-id="43edc-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="43edc-129">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="43edc-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="43edc-130">\<id ></span><span class="sxs-lookup"><span data-stu-id="43edc-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
