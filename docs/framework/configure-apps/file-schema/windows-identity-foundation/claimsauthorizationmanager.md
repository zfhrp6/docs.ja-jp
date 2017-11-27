---
title: '&lt;claimsAuthorizationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4b4d86204d5f7225f167be125ce017488c851e98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthorizationmanagergt"></a><span data-ttu-id="9aa95-102">&lt;claimsAuthorizationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="9aa95-102">&lt;claimsAuthorizationManager&gt;</span></span>
<span data-ttu-id="9aa95-103">入力方向の要求の要求の承認マネージャーを登録します。</span><span class="sxs-lookup"><span data-stu-id="9aa95-103">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="9aa95-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="9aa95-104">\<system.identityModel></span></span>  
<span data-ttu-id="9aa95-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9aa95-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9aa95-106">\<claimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="9aa95-106">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa95-107">構文</span><span class="sxs-lookup"><span data-stu-id="9aa95-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9aa95-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9aa95-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9aa95-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9aa95-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aa95-110">属性</span><span class="sxs-lookup"><span data-stu-id="9aa95-110">Attributes</span></span>  
  
|<span data-ttu-id="9aa95-111">属性</span><span class="sxs-lookup"><span data-stu-id="9aa95-111">Attribute</span></span>|<span data-ttu-id="9aa95-112">説明</span><span class="sxs-lookup"><span data-stu-id="9aa95-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9aa95-113">型</span><span class="sxs-lookup"><span data-stu-id="9aa95-113">type</span></span>|<span data-ttu-id="9aa95-114">派生するカスタム型、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラスです。</span><span class="sxs-lookup"><span data-stu-id="9aa95-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="9aa95-115">指定する方法について、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9aa95-115">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9aa95-116">子要素</span><span class="sxs-lookup"><span data-stu-id="9aa95-116">Child Elements</span></span>  
 <span data-ttu-id="9aa95-117">ある場合ありません`type`属性、または、`type`属性参照、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthorizationManager>`要素が子要素を受け取らないです。 ただし、から派生したクラス<xref:System.Security.Claims.ClaimsAuthorizationManager>子の構成要素を定義できます。</span><span class="sxs-lookup"><span data-stu-id="9aa95-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9aa95-118">親要素</span><span class="sxs-lookup"><span data-stu-id="9aa95-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9aa95-119">要素</span><span class="sxs-lookup"><span data-stu-id="9aa95-119">Element</span></span>|<span data-ttu-id="9aa95-120">説明</span><span class="sxs-lookup"><span data-stu-id="9aa95-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aa95-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9aa95-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="9aa95-122">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="9aa95-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aa95-123">コメント</span><span class="sxs-lookup"><span data-stu-id="9aa95-123">Remarks</span></span>  
 <span data-ttu-id="9aa95-124">によって提供される既定の動作、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラスは常に入力方向の要求を承認します。</span><span class="sxs-lookup"><span data-stu-id="9aa95-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="9aa95-125">ない場合は`type`属性が指定されて場合、または、`type`属性を指定、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラス、`<claimsAuthorizationManager>`要素は子要素を取りません。</span><span class="sxs-lookup"><span data-stu-id="9aa95-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="9aa95-126">指定することができます、`type`から派生した型を登録する属性、<xref:System.Security.Claims.ClaimsAuthorizationManager>カスタム動作を実装するクラス。</span><span class="sxs-lookup"><span data-stu-id="9aa95-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="9aa95-127">派生クラスの子要素から構成をサポートできる、`<claimsAuthorizationManager>`要素をオーバーライドすることで、<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>これらの要素を処理するメソッド。</span><span class="sxs-lookup"><span data-stu-id="9aa95-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="9aa95-128">子要素に定義されたスキーマは、クラスの設計者の責任です。</span><span class="sxs-lookup"><span data-stu-id="9aa95-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9aa95-129">使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コードによって参照される id の構成でクレーム ベースのアクセス制御を提供するクラス、`<federationConfiguration>`要素は、要求承認マネージャーとを使用して、ポリシーを構成します。承認を決定します。</span><span class="sxs-lookup"><span data-stu-id="9aa95-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="9aa95-130">これは、true の場合、パッシブの Web シナリオ、たとえば、Windows Communication Foundation (WCF) アプリケーションや Web ベースではないアプリケーションではないシナリオであってもです。</span><span class="sxs-lookup"><span data-stu-id="9aa95-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="9aa95-131">アプリケーションが、パッシブ Web アプリケーションではない場合、`<claimsAuthorizationManager>`要素 (とその子ポリシー要素、存在する場合) のみに適用される設定は、参照される id の構成のです。</span><span class="sxs-lookup"><span data-stu-id="9aa95-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="9aa95-132">その他のすべての設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9aa95-132">All other settings are ignored.</span></span> <span data-ttu-id="9aa95-133">詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="9aa95-133">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="9aa95-134">この要素の設定、<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9aa95-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aa95-135">例</span><span class="sxs-lookup"><span data-stu-id="9aa95-135">Example</span></span>  
 <span data-ttu-id="9aa95-136">次の XML では、それぞれ指定するブール型の組み合わせ申請元がリソースに対してアクションを実行する処理する必要をクレームのリソース操作のペアから成るポリシーを実装するマネージャー要求承認の構成を示します。</span><span class="sxs-lookup"><span data-stu-id="9aa95-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="9aa95-137">このポリシーを使用できる要求の承認マネージャーを実装するコードは含まれて、`ClaimsBasedAuthorization`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9aa95-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
