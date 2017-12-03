---
title: "&lt;authorizationPolicies&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a039500281f02aa6ae891065255174c2353ba33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="74d95-102">&lt;authorizationPolicies&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="74d95-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="74d95-103">クレームの変換の承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="74d95-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="74d95-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="74d95-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="74d95-105">\<behaviors></span></span>  
<span data-ttu-id="74d95-106">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="74d95-106">\<behavior></span></span>  
<span data-ttu-id="74d95-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="74d95-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="74d95-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="74d95-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="74d95-109">\<add></span><span class="sxs-lookup"><span data-stu-id="74d95-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d95-110">構文</span><span class="sxs-lookup"><span data-stu-id="74d95-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="74d95-111">型</span><span class="sxs-lookup"><span data-stu-id="74d95-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74d95-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="74d95-112">Attributes and Elements</span></span>  
 <span data-ttu-id="74d95-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="74d95-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74d95-114">属性</span><span class="sxs-lookup"><span data-stu-id="74d95-114">Attributes</span></span>  
  
|<span data-ttu-id="74d95-115">属性</span><span class="sxs-lookup"><span data-stu-id="74d95-115">Attribute</span></span>|<span data-ttu-id="74d95-116">説明</span><span class="sxs-lookup"><span data-stu-id="74d95-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="74d95-117">必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="74d95-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="74d95-118">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アクセス制御モデルは、承認ポリシーのセットを型として提供します。</span><span class="sxs-lookup"><span data-stu-id="74d95-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="74d95-119">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="74d95-120">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="74d95-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74d95-121">子要素</span><span class="sxs-lookup"><span data-stu-id="74d95-121">Child Elements</span></span>  
 <span data-ttu-id="74d95-122">なし。</span><span class="sxs-lookup"><span data-stu-id="74d95-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74d95-123">親要素</span><span class="sxs-lookup"><span data-stu-id="74d95-123">Parent Elements</span></span>  
  
|<span data-ttu-id="74d95-124">要素</span><span class="sxs-lookup"><span data-stu-id="74d95-124">Element</span></span>|<span data-ttu-id="74d95-125">説明</span><span class="sxs-lookup"><span data-stu-id="74d95-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74d95-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="74d95-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="74d95-127">承認ポリシーの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74d95-128">コメント</span><span class="sxs-lookup"><span data-stu-id="74d95-128">Remarks</span></span>  
 <span data-ttu-id="74d95-129">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="74d95-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="74d95-130">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="74d95-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="74d95-131">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="74d95-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="74d95-132">承認ポリシーのしくみの詳細については、次を参照してください。<xref:System.IdentityModel.Policy.IAuthorizationPolicy>と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="74d95-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d95-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="74d95-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="74d95-134">サービス操作へのアクセスを承認します。</span><span class="sxs-lookup"><span data-stu-id="74d95-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="74d95-135">方法: サービスのカスタム承認マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="74d95-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="74d95-136">\<add></span><span class="sxs-lookup"><span data-stu-id="74d95-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="74d95-137">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="74d95-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
