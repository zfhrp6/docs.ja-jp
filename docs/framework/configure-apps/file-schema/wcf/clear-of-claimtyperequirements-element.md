---
title: "&lt;claimTypeRequirements&gt; 要素の &lt;clear&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a5c3b101c51bcba1c1a579dcf99001c4b8dbab2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="b3ed2-102">&lt;claimTypeRequirements&gt; 要素の &lt;clear&gt;</span><span class="sxs-lookup"><span data-stu-id="b3ed2-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="b3ed2-103">すべてのクレームの種類をフェデレーション資格情報から削除するように指定します。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="b3ed2-104">これにより、コレクションの初期値を確実に空にできます。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="b3ed2-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b3ed2-106">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-106">\<bindings></span></span>  
<span data-ttu-id="b3ed2-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="b3ed2-108">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-108">\<binding></span></span>  
<span data-ttu-id="b3ed2-109">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-109">\<security></span></span>  
<span data-ttu-id="b3ed2-110">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-110">\<message></span></span>  
<span data-ttu-id="b3ed2-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ed2-112">構文</span><span class="sxs-lookup"><span data-stu-id="b3ed2-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3ed2-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b3ed2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b3ed2-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3ed2-115">属性</span><span class="sxs-lookup"><span data-stu-id="b3ed2-115">Attributes</span></span>  
 <span data-ttu-id="b3ed2-116">なし。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b3ed2-117">子要素</span><span class="sxs-lookup"><span data-stu-id="b3ed2-117">Child Elements</span></span>  
 <span data-ttu-id="b3ed2-118">なし。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3ed2-119">親要素</span><span class="sxs-lookup"><span data-stu-id="b3ed2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b3ed2-120">要素</span><span class="sxs-lookup"><span data-stu-id="b3ed2-120">Element</span></span>|<span data-ttu-id="b3ed2-121">説明</span><span class="sxs-lookup"><span data-stu-id="b3ed2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3ed2-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="b3ed2-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="b3ed2-123">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="b3ed2-124">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="b3ed2-125">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b3ed2-126">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b3ed2-127">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="b3ed2-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3ed2-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3ed2-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
