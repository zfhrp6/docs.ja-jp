---
title: "&lt;serviceCredentials&gt; の &lt;windowsAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8af7d89fdf09316594bc8ef3433e2b47e8fb0a7e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="6c9d3-102">&lt;serviceCredentials&gt; の &lt;windowsAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="6c9d3-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="6c9d3-103">Windows サービス資格情報の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="6c9d3-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c9d3-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-105">\<behaviors></span></span>  
<span data-ttu-id="6c9d3-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6c9d3-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-107">\<behavior></span></span>  
<span data-ttu-id="6c9d3-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-108">\<serviceCredentials></span></span>  
<span data-ttu-id="6c9d3-109">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9d3-110">構文</span><span class="sxs-lookup"><span data-stu-id="6c9d3-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c9d3-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6c9d3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6c9d3-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c9d3-113">属性</span><span class="sxs-lookup"><span data-stu-id="6c9d3-113">Attributes</span></span>  
  
|<span data-ttu-id="6c9d3-114">属性</span><span class="sxs-lookup"><span data-stu-id="6c9d3-114">Attribute</span></span>|<span data-ttu-id="6c9d3-115">説明</span><span class="sxs-lookup"><span data-stu-id="6c9d3-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="6c9d3-116">セキュリティ コンテキストに Windows グループが含まれるかどうかを指定する省略可能なブール属性。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="6c9d3-117">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="6c9d3-118">この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="6c9d3-119">ユーザーが属するグループの一覧を生成する必要がない場合は、この属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="6c9d3-120">認証されていない匿名の呼び出し元を許可するかどうかを指定する省略可能なブール属性。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="6c9d3-121">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6c9d3-122">バインディングの `clientCredentialType` 属性が `Windows` に設定されている場合、匿名の呼び出し元は許可されません。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="6c9d3-123">これは、ドメインまたはワークグループの認証済み呼び出し元だけがシステムへのアクセスを許可されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="6c9d3-124">この動作は、この属性を使用してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="6c9d3-125">この設定を使用するときは十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c9d3-126">子要素</span><span class="sxs-lookup"><span data-stu-id="6c9d3-126">Child Elements</span></span>  
 <span data-ttu-id="6c9d3-127">なし。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c9d3-128">親要素</span><span class="sxs-lookup"><span data-stu-id="6c9d3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6c9d3-129">要素</span><span class="sxs-lookup"><span data-stu-id="6c9d3-129">Element</span></span>|<span data-ttu-id="6c9d3-130">説明</span><span class="sxs-lookup"><span data-stu-id="6c9d3-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c9d3-131">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="6c9d3-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="6c9d3-132">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c9d3-133">コメント</span><span class="sxs-lookup"><span data-stu-id="6c9d3-133">Remarks</span></span>  
 <span data-ttu-id="6c9d3-134">匿名の Windows ユーザーのアクセスを許可するかどうかを指定するには、この要素を使用して、`allowAnonymousLogons` 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="6c9d3-135">また、`includeWindowsGroups` 属性を設定すると、ユーザーが属するグループの情報を AuthorizationContext に含めるかどうかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="6c9d3-136">この属性が `true` (既定値) に設定されている場合、サービスはクライアントが属している Windows グループを特定できます。</span><span class="sxs-lookup"><span data-stu-id="6c9d3-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9d3-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c9d3-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
