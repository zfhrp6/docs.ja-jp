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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d835d96c89e8b292fc2c038794aa4056fda3a095
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="e737f-102">&lt;authorizationPolicies&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="e737f-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="e737f-103">クレームの変換の承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e737f-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="e737f-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e737f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e737f-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e737f-105">\<behaviors></span></span>  
<span data-ttu-id="e737f-106">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e737f-106">\<behavior></span></span>  
<span data-ttu-id="e737f-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="e737f-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="e737f-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="e737f-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="e737f-109">\<add></span><span class="sxs-lookup"><span data-stu-id="e737f-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e737f-110">構文</span><span class="sxs-lookup"><span data-stu-id="e737f-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="e737f-111">型</span><span class="sxs-lookup"><span data-stu-id="e737f-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e737f-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e737f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e737f-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e737f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e737f-114">属性</span><span class="sxs-lookup"><span data-stu-id="e737f-114">Attributes</span></span>  
  
|<span data-ttu-id="e737f-115">属性</span><span class="sxs-lookup"><span data-stu-id="e737f-115">Attribute</span></span>|<span data-ttu-id="e737f-116">説明</span><span class="sxs-lookup"><span data-stu-id="e737f-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="e737f-117">必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="e737f-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="e737f-118">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アクセス制御モデルは、承認ポリシーのセットを型として提供します。</span><span class="sxs-lookup"><span data-stu-id="e737f-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="e737f-119">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e737f-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e737f-120">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e737f-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e737f-121">子要素</span><span class="sxs-lookup"><span data-stu-id="e737f-121">Child Elements</span></span>  
 <span data-ttu-id="e737f-122">なし。</span><span class="sxs-lookup"><span data-stu-id="e737f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e737f-123">親要素</span><span class="sxs-lookup"><span data-stu-id="e737f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e737f-124">要素</span><span class="sxs-lookup"><span data-stu-id="e737f-124">Element</span></span>|<span data-ttu-id="e737f-125">説明</span><span class="sxs-lookup"><span data-stu-id="e737f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e737f-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="e737f-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="e737f-127">承認ポリシーの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e737f-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e737f-128">コメント</span><span class="sxs-lookup"><span data-stu-id="e737f-128">Remarks</span></span>  
 <span data-ttu-id="e737f-129">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="e737f-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="e737f-130">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e737f-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e737f-131">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e737f-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="e737f-132">承認ポリシーのしくみの詳細については、次を参照してください。<xref:System.IdentityModel.Policy.IAuthorizationPolicy>と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="e737f-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e737f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e737f-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="e737f-134">サービス操作へのアクセスを承認します。</span><span class="sxs-lookup"><span data-stu-id="e737f-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="e737f-135">方法: サービスのカスタム承認マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e737f-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="e737f-136">\<add></span><span class="sxs-lookup"><span data-stu-id="e737f-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="e737f-137">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="e737f-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
