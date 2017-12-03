---
title: "&lt;claimTypeRequirements&gt; 要素の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc644648ad244eb642f96fdc93213fbd38152f48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="2c654-102">&lt;claimTypeRequirements&gt; 要素の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="2c654-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="2c654-103">フェデレーション資格情報に表示されると予想される必須のクレームおよび省略可能なクレームの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c654-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="2c654-104">たとえば、サービスは、クレームの種類の特定のセットを処理する必要がある受信資格情報について要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="2c654-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="2c654-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2c654-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2c654-106">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2c654-106">\<bindings></span></span>  
<span data-ttu-id="2c654-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="2c654-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="2c654-108">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2c654-108">\<binding></span></span>  
<span data-ttu-id="2c654-109">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="2c654-109">\<security></span></span>  
<span data-ttu-id="2c654-110">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="2c654-110">\<message></span></span>  
<span data-ttu-id="2c654-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2c654-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c654-112">構文</span><span class="sxs-lookup"><span data-stu-id="2c654-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c654-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2c654-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2c654-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c654-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c654-115">属性</span><span class="sxs-lookup"><span data-stu-id="2c654-115">Attributes</span></span>  
  
|<span data-ttu-id="2c654-116">属性</span><span class="sxs-lookup"><span data-stu-id="2c654-116">Attribute</span></span>|<span data-ttu-id="2c654-117">説明</span><span class="sxs-lookup"><span data-stu-id="2c654-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c654-118">claimType</span><span class="sxs-lookup"><span data-stu-id="2c654-118">claimType</span></span>|<span data-ttu-id="2c654-119">クレームの種類を定義する URI。</span><span class="sxs-lookup"><span data-stu-id="2c654-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="2c654-120">たとえば、Web サイトから製品を購入するために、ユーザーは、十分な与信限度額を備えた有効なクレジット カードを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c654-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="2c654-121">クレームの種類として、クレジット カードの URI があります。</span><span class="sxs-lookup"><span data-stu-id="2c654-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="2c654-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="2c654-122">isOptional</span></span>|<span data-ttu-id="2c654-123">これが省略可能なクレームかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="2c654-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="2c654-124">これが必須のクレームの場合は、この属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="2c654-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="2c654-125">サービスが必須でない情報を求めるときにこの属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c654-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="2c654-126">たとえば、ユーザーに氏名と住所の入力を要求し、電話番号は省略可能にする場合などです。</span><span class="sxs-lookup"><span data-stu-id="2c654-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c654-127">子要素</span><span class="sxs-lookup"><span data-stu-id="2c654-127">Child Elements</span></span>  
 <span data-ttu-id="2c654-128">なし。</span><span class="sxs-lookup"><span data-stu-id="2c654-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c654-129">親要素</span><span class="sxs-lookup"><span data-stu-id="2c654-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2c654-130">要素</span><span class="sxs-lookup"><span data-stu-id="2c654-130">Element</span></span>|<span data-ttu-id="2c654-131">説明</span><span class="sxs-lookup"><span data-stu-id="2c654-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c654-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2c654-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="2c654-133">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c654-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="2c654-134">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="2c654-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="2c654-135">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="2c654-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2c654-136">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c654-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2c654-137">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c654-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c654-138">コメント</span><span class="sxs-lookup"><span data-stu-id="2c654-138">Remarks</span></span>  
 <span data-ttu-id="2c654-139">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="2c654-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2c654-140">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c654-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2c654-141">この要件はセキュリティ ポリシー内に明記されます。</span><span class="sxs-lookup"><span data-stu-id="2c654-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="2c654-142">クライアントがフェデレーション サービスの資格情報 (CardSpace など) を要求する場合、クライアントは要件をトークン要求 (RequestSecurityToken) に設定します。これにより、フェデレーション サービスは、要件どおりの資格情報を発行できます。</span><span class="sxs-lookup"><span data-stu-id="2c654-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c654-143">例</span><span class="sxs-lookup"><span data-stu-id="2c654-143">Example</span></span>  
 <span data-ttu-id="2c654-144">次の構成では、2 つのクレームの種類の要件をセキュリティ バインディングに追加しています。</span><span class="sxs-lookup"><span data-stu-id="2c654-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c654-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c654-145">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
