---
title: '&lt;authorizationPolicies&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 008f465134860141293776130ebd75cd39120f5e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="2a2ff-102">&lt;authorizationPolicies&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="2a2ff-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="2a2ff-103">クレームの変換の承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="2a2ff-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2a2ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a2ff-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="2a2ff-105">\<behaviors></span></span>  
<span data-ttu-id="2a2ff-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2a2ff-106">\<behavior></span></span>  
<span data-ttu-id="2a2ff-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="2a2ff-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="2a2ff-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="2a2ff-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="2a2ff-109">\<add></span><span class="sxs-lookup"><span data-stu-id="2a2ff-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a2ff-110">構文</span><span class="sxs-lookup"><span data-stu-id="2a2ff-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="2a2ff-111">型</span><span class="sxs-lookup"><span data-stu-id="2a2ff-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a2ff-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2a2ff-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2a2ff-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a2ff-114">属性</span><span class="sxs-lookup"><span data-stu-id="2a2ff-114">Attributes</span></span>  
  
|<span data-ttu-id="2a2ff-115">属性</span><span class="sxs-lookup"><span data-stu-id="2a2ff-115">Attribute</span></span>|<span data-ttu-id="2a2ff-116">説明</span><span class="sxs-lookup"><span data-stu-id="2a2ff-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="2a2ff-117">必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="2a2ff-118">Windows Communication Foundation (WCF) のアクセス制御モデルでは、一連の型として承認ポリシーのプロビジョニングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="2a2ff-119">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="2a2ff-120">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a2ff-121">子要素</span><span class="sxs-lookup"><span data-stu-id="2a2ff-121">Child Elements</span></span>  
 <span data-ttu-id="2a2ff-122">なし。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a2ff-123">親要素</span><span class="sxs-lookup"><span data-stu-id="2a2ff-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2a2ff-124">要素</span><span class="sxs-lookup"><span data-stu-id="2a2ff-124">Element</span></span>|<span data-ttu-id="2a2ff-125">説明</span><span class="sxs-lookup"><span data-stu-id="2a2ff-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a2ff-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="2a2ff-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="2a2ff-127">承認ポリシーの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a2ff-128">コメント</span><span class="sxs-lookup"><span data-stu-id="2a2ff-128">Remarks</span></span>  
 <span data-ttu-id="2a2ff-129">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="2a2ff-130">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="2a2ff-131">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="2a2ff-132">承認ポリシーのしくみの詳細については、次を参照してください。<xref:System.IdentityModel.Policy.IAuthorizationPolicy>と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a2ff-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2ff-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a2ff-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="2a2ff-134">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="2a2ff-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="2a2ff-135">方法 : サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="2a2ff-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="2a2ff-136">\<add></span><span class="sxs-lookup"><span data-stu-id="2a2ff-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="2a2ff-137">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="2a2ff-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
