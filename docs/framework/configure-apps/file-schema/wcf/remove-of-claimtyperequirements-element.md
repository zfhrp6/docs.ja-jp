---
title: "&lt;claimTypeRequirements&gt; 要素の &lt;remove&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dde956ab80a41d15a6496f84432a2ae2a9d09b76
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="5d748-102">&lt;claimTypeRequirements&gt; 要素の &lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="5d748-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="5d748-103">フェデレーション資格情報から削除するクレームの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5d748-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="5d748-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5d748-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5d748-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="5d748-105">\<bindings></span></span>  
<span data-ttu-id="5d748-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="5d748-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="5d748-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="5d748-107">\<binding></span></span>  
<span data-ttu-id="5d748-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="5d748-108">\<security></span></span>  
<span data-ttu-id="5d748-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="5d748-109">\<message></span></span>  
<span data-ttu-id="5d748-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="5d748-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d748-111">構文</span><span class="sxs-lookup"><span data-stu-id="5d748-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d748-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5d748-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5d748-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d748-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d748-114">属性</span><span class="sxs-lookup"><span data-stu-id="5d748-114">Attributes</span></span>  
  
|<span data-ttu-id="5d748-115">属性</span><span class="sxs-lookup"><span data-stu-id="5d748-115">Attribute</span></span>|<span data-ttu-id="5d748-116">説明</span><span class="sxs-lookup"><span data-stu-id="5d748-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d748-117">claimType</span><span class="sxs-lookup"><span data-stu-id="5d748-117">claimType</span></span>|<span data-ttu-id="5d748-118">削除するクレームの種類を定義する URI。</span><span class="sxs-lookup"><span data-stu-id="5d748-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d748-119">子要素</span><span class="sxs-lookup"><span data-stu-id="5d748-119">Child Elements</span></span>  
 <span data-ttu-id="5d748-120">なし。</span><span class="sxs-lookup"><span data-stu-id="5d748-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d748-121">親要素</span><span class="sxs-lookup"><span data-stu-id="5d748-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5d748-122">要素</span><span class="sxs-lookup"><span data-stu-id="5d748-122">Element</span></span>|<span data-ttu-id="5d748-123">説明</span><span class="sxs-lookup"><span data-stu-id="5d748-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d748-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="5d748-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="5d748-125">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d748-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="5d748-126">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="5d748-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="5d748-127">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="5d748-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5d748-128">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d748-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5d748-129">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5d748-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d748-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d748-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
