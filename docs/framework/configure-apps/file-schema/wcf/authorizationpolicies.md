---
title: '&lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e33dca28f11b564f622ff1c202827c693f0874c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltauthorizationpoliciesgt"></a><span data-ttu-id="0ac6d-102">&lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="0ac6d-102">&lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="0ac6d-103">この構成セクションには、`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ac6d-103">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="0ac6d-104">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="0ac6d-104">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="0ac6d-105">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="0ac6d-105">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="0ac6d-106">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="0ac6d-106">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="0ac6d-107">承認ポリシーのしくみの詳細については、次を参照してください。<xref:System.IdentityModel.Policy.IAuthorizationPolicy>と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ac6d-107">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac6d-108">参照</span><span class="sxs-lookup"><span data-stu-id="0ac6d-108">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="0ac6d-109">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="0ac6d-109">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="0ac6d-110">方法 : サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="0ac6d-110">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="0ac6d-111">\<add></span><span class="sxs-lookup"><span data-stu-id="0ac6d-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="0ac6d-112">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="0ac6d-112">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
