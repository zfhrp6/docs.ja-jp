---
title: '&lt;authorizationPolicies&gt;'
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 8e1bc702db899c4b0b3ee539fdc89cdda6c4cf10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltauthorizationpoliciesgt"></a><span data-ttu-id="aab8b-102">&lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="aab8b-102">&lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="aab8b-103">この構成セクションには、`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aab8b-103">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="aab8b-104">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="aab8b-104">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="aab8b-105">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="aab8b-105">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="aab8b-106">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="aab8b-106">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="aab8b-107">承認ポリシーのしくみの詳細については、次を参照してください。<xref:System.IdentityModel.Policy.IAuthorizationPolicy>と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="aab8b-107">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab8b-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="aab8b-108">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="aab8b-109">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="aab8b-109">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="aab8b-110">方法 : サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="aab8b-110">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="aab8b-111">\<add></span><span class="sxs-lookup"><span data-stu-id="aab8b-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="aab8b-112">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="aab8b-112">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
