---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 909df1bd6054d9737f91c30c3c6b2d68b932281c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="d644f-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="d644f-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="d644f-103">クレームを定義する、ロールの種類のコレクション内の要求の種類を指定<xref:System.Security.Claims.ClaimsIdentity>によって返されるオブジェクト、<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>トークン ハンドラーのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d644f-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="d644f-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d644f-104">\<system.identityModel></span></span>  
<span data-ttu-id="d644f-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d644f-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d644f-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d644f-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d644f-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d644f-107">\<add></span></span>  
<span data-ttu-id="d644f-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d644f-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="d644f-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="d644f-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d644f-110">構文</span><span class="sxs-lookup"><span data-stu-id="d644f-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d644f-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d644f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d644f-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d644f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d644f-113">属性</span><span class="sxs-lookup"><span data-stu-id="d644f-113">Attributes</span></span>  
  
|<span data-ttu-id="d644f-114">属性</span><span class="sxs-lookup"><span data-stu-id="d644f-114">Attribute</span></span>|<span data-ttu-id="d644f-115">説明</span><span class="sxs-lookup"><span data-stu-id="d644f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d644f-116">value</span><span class="sxs-lookup"><span data-stu-id="d644f-116">value</span></span>|<span data-ttu-id="d644f-117">ロール クレームの種類を使用する要求の要求の種類を表す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d644f-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d644f-118">子要素</span><span class="sxs-lookup"><span data-stu-id="d644f-118">Child Elements</span></span>  
 <span data-ttu-id="d644f-119">なし</span><span class="sxs-lookup"><span data-stu-id="d644f-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d644f-120">親要素</span><span class="sxs-lookup"><span data-stu-id="d644f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d644f-121">要素</span><span class="sxs-lookup"><span data-stu-id="d644f-121">Element</span></span>|<span data-ttu-id="d644f-122">説明</span><span class="sxs-lookup"><span data-stu-id="d644f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d644f-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d644f-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="d644f-124">構成を提供、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラス。</span><span class="sxs-lookup"><span data-stu-id="d644f-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d644f-125">コメント</span><span class="sxs-lookup"><span data-stu-id="d644f-125">Remarks</span></span>  
 <span data-ttu-id="d644f-126">`<roleClaimType>`要素セット、<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>プロパティと、<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>構成からオブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="d644f-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d644f-127">例</span><span class="sxs-lookup"><span data-stu-id="d644f-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d644f-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d644f-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
