---
title: '&lt;userNameAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea18a2c8c2244f384b87b48f195b77da4eb5dfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="7d0f0-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="7d0f0-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="7d0f0-103">ユーザー名とパスワードに基づいてサービスの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="7d0f0-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d0f0-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-105">\<behaviors></span></span>  
<span data-ttu-id="7d0f0-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7d0f0-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-107">\<behavior></span></span>  
<span data-ttu-id="7d0f0-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7d0f0-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d0f0-110">構文</span><span class="sxs-lookup"><span data-stu-id="7d0f0-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d0f0-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7d0f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7d0f0-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d0f0-113">属性</span><span class="sxs-lookup"><span data-stu-id="7d0f0-113">Attributes</span></span>  
  
|<span data-ttu-id="7d0f0-114">属性</span><span class="sxs-lookup"><span data-stu-id="7d0f0-114">Attribute</span></span>|<span data-ttu-id="7d0f0-115">説明</span><span class="sxs-lookup"><span data-stu-id="7d0f0-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="7d0f0-116">トークンがキャッシュ内に保持される最大時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="7d0f0-117">既定値は 00:15:00 です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="7d0f0-118">ログオン トークンがキャッシュされるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="7d0f0-119">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="7d0f0-120">使用されるカスタム ユーザー名およびパスワード検証の種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="7d0f0-121">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="7d0f0-122">セキュリティ コンテキストに Windows グループが含まれるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="7d0f0-123">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="7d0f0-124">この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="7d0f0-125">ユーザーが属するグループの一覧を生成する必要がない場合は、このプロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="7d0f0-126">キャッシュするログオン トークンの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="7d0f0-127">この値は、ゼロより大きい値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-127">This value should be larger than zero.</span></span> <span data-ttu-id="7d0f0-128">既定値は 128 です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="7d0f0-129">バインディングの `clientCredentialType` 属性が `username` に設定されている場合、ユーザー名は Windows アカウントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="7d0f0-130">関連するパスワード検証機構を提供する <xref:System.Web.Security.MembershipProvider> 値の名前を含む文字列であるこの属性を使用して動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="7d0f0-131">ユーザー名とパスワードを検証する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="7d0f0-132">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="7d0f0-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="7d0f0-133">-   Windows</span></span><br /><span data-ttu-id="7d0f0-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="7d0f0-134">-   MembershipProvider</span></span><br /><span data-ttu-id="7d0f0-135">-カスタム</span><span class="sxs-lookup"><span data-stu-id="7d0f0-135">-   Custom</span></span><br /><br /> <span data-ttu-id="7d0f0-136">既定は Windows です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-136">The default is Windows.</span></span> <span data-ttu-id="7d0f0-137">この属性は <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d0f0-138">子要素</span><span class="sxs-lookup"><span data-stu-id="7d0f0-138">Child Elements</span></span>  
 <span data-ttu-id="7d0f0-139">なし。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d0f0-140">親要素</span><span class="sxs-lookup"><span data-stu-id="7d0f0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="7d0f0-141">要素</span><span class="sxs-lookup"><span data-stu-id="7d0f0-141">Element</span></span>|<span data-ttu-id="7d0f0-142">説明</span><span class="sxs-lookup"><span data-stu-id="7d0f0-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d0f0-143">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7d0f0-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="7d0f0-144">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d0f0-145">コメント</span><span class="sxs-lookup"><span data-stu-id="7d0f0-145">Remarks</span></span>  
 <span data-ttu-id="7d0f0-146">サービスで使用されるバインディングがユーザー名とパスワード ベースの認証を使用するように構成されていない場合、この要素の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="7d0f0-147">これには、`customUserNamePasswordValidatorType`、`includeWindowsGroups`、`membershipProviderName`、および `userNamePasswordValidationMode` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="7d0f0-148">サービスで使用されるバインディングが Windows 認証のユーザー名とパスワードを使用するように構成されていない場合、ログオン トークンのキャッシュに関連する設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="7d0f0-149">これには、`cacheLogonTokenLifetime`、`cacheLogonTokens`、および `maxCacheLogonTokens`、が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7d0f0-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d0f0-150">参照</span><span class="sxs-lookup"><span data-stu-id="7d0f0-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
