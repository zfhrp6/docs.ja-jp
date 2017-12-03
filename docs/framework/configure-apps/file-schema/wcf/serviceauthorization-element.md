---
title: "&lt;serviceAuthorization&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc04552b9b2ecd85a520ed16ae9a6ee0dfc98a46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthorizationgt-element"></a><span data-ttu-id="1ee71-102">&lt;serviceAuthorization&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="1ee71-102">&lt;serviceAuthorization&gt; element</span></span>
<span data-ttu-id="1ee71-103">サービス操作へのアクセスを許可する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="1ee71-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1ee71-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ee71-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="1ee71-105">\<behaviors></span></span>  
<span data-ttu-id="1ee71-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1ee71-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1ee71-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1ee71-107">\<behavior></span></span>  
<span data-ttu-id="1ee71-108">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="1ee71-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee71-109">構文</span><span class="sxs-lookup"><span data-stu-id="1ee71-109">Syntax</span></span>  
  
```xml  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ee71-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1ee71-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ee71-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ee71-112">属性</span><span class="sxs-lookup"><span data-stu-id="1ee71-112">Attributes</span></span>  
  
|<span data-ttu-id="1ee71-113">属性</span><span class="sxs-lookup"><span data-stu-id="1ee71-113">Attribute</span></span>|<span data-ttu-id="1ee71-114">説明</span><span class="sxs-lookup"><span data-stu-id="1ee71-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ee71-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="1ee71-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="1ee71-116">サービスのすべての操作が呼び出し元を偽装するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="1ee71-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="1ee71-117">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="1ee71-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1ee71-118">特定のサービス操作が呼び出し元を偽装する場合、スレッド コンテキストは、指定されたサービスを実行する前に呼び出し元のコンテキストに切り替えられます。</span><span class="sxs-lookup"><span data-stu-id="1ee71-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="1ee71-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="1ee71-119">principalPermissionMode</span></span>|<span data-ttu-id="1ee71-120">サーバーでの操作を実行するために使用されるプリンシパルを設定します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="1ee71-121">次の値があります。</span><span class="sxs-lookup"><span data-stu-id="1ee71-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="1ee71-122">-なし</span><span class="sxs-lookup"><span data-stu-id="1ee71-122">-   None</span></span><br /><span data-ttu-id="1ee71-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="1ee71-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="1ee71-124">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="1ee71-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="1ee71-125">-カスタム</span><span class="sxs-lookup"><span data-stu-id="1ee71-125">-   Custom</span></span><br /><br /> <span data-ttu-id="1ee71-126">既定値は UseWindowsGroups です。</span><span class="sxs-lookup"><span data-stu-id="1ee71-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="1ee71-127">値は、<xref:System.ServiceModel.Description.PrincipalPermissionMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="1ee71-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="1ee71-128">この属性の使用の詳細については、次を参照してください。[する方法: PrincipalPermissionAttribute クラスを使用したアクセスの制限](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ee71-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="1ee71-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="1ee71-129">roleProviderName</span></span>|<span data-ttu-id="1ee71-130">Windows Communication Foundation (WCF) アプリケーションにロール情報を提供するロール プロバイダーの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="1ee71-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1ee71-131">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="1ee71-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="1ee71-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="1ee71-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="1ee71-133">サービス承認マネージャーの型を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="1ee71-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="1ee71-134">詳細については、「<xref:System.ServiceModel.ServiceAuthorizationManager>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ee71-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ee71-135">子要素</span><span class="sxs-lookup"><span data-stu-id="1ee71-135">Child Elements</span></span>  
  
|<span data-ttu-id="1ee71-136">要素</span><span class="sxs-lookup"><span data-stu-id="1ee71-136">Element</span></span>|<span data-ttu-id="1ee71-137">説明</span><span class="sxs-lookup"><span data-stu-id="1ee71-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ee71-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="1ee71-138">authorizationPolicies</span></span>|<span data-ttu-id="1ee71-139">`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="1ee71-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="1ee71-140">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="1ee71-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="1ee71-141">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="1ee71-142">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="1ee71-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="1ee71-143">詳細については、「<xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ee71-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ee71-144">親要素</span><span class="sxs-lookup"><span data-stu-id="1ee71-144">Parent Elements</span></span>  
  
|<span data-ttu-id="1ee71-145">要素</span><span class="sxs-lookup"><span data-stu-id="1ee71-145">Element</span></span>|<span data-ttu-id="1ee71-146">説明</span><span class="sxs-lookup"><span data-stu-id="1ee71-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ee71-147">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1ee71-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1ee71-148">サービスの動作設定のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ee71-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ee71-149">コメント</span><span class="sxs-lookup"><span data-stu-id="1ee71-149">Remarks</span></span>  
 <span data-ttu-id="1ee71-150">このセクションには、承認、カスタム ロール プロバイダー、および偽装に影響する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ee71-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="1ee71-151">`principalPermissionMode` 属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="1ee71-152">既定値は `UseWindowsGroups` で、リソースにアクセスしようとしている ID を、"Administrators" や "Users" などの Windows グループから検索するように指定します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="1ee71-153">指定することも`UseAspNetRoles`の下で構成されるカスタム ロール プロバイダーを使用する、 \<system.web > 要素を次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="1ee71-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 <span data-ttu-id="1ee71-154">`roleProviderName` 属性で `principalPermissionMode` を使用する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 <span data-ttu-id="1ee71-155">この構成要素を使用する詳細な例についてを参照してください。[サービス操作へのアクセスを承認する](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ee71-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee71-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ee71-156">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [<span data-ttu-id="1ee71-157">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="1ee71-157">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1ee71-158">サービス操作へのアクセスを承認します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-158">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="1ee71-159">方法: サービスのカスタム承認マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ee71-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="1ee71-160">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="1ee71-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [<span data-ttu-id="1ee71-161">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="1ee71-161">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
