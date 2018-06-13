---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 86a9b9dcf0b9f5971e50ff7d1f1c37ca2e5f778a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756528"
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="993dd-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="993dd-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="993dd-103">構成を提供、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラス。</span><span class="sxs-lookup"><span data-stu-id="993dd-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="993dd-104">によって表される、<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="993dd-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="993dd-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="993dd-105">\<system.identityModel></span></span>  
<span data-ttu-id="993dd-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="993dd-106">\<identityConfiguration></span></span>  
<span data-ttu-id="993dd-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="993dd-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="993dd-108">\<add></span><span class="sxs-lookup"><span data-stu-id="993dd-108">\<add></span></span>  
<span data-ttu-id="993dd-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="993dd-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993dd-110">構文</span><span class="sxs-lookup"><span data-stu-id="993dd-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="993dd-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="993dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="993dd-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="993dd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="993dd-113">属性</span><span class="sxs-lookup"><span data-stu-id="993dd-113">Attributes</span></span>  
  
|<span data-ttu-id="993dd-114">属性</span><span class="sxs-lookup"><span data-stu-id="993dd-114">Attribute</span></span>|<span data-ttu-id="993dd-115">説明</span><span class="sxs-lookup"><span data-stu-id="993dd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="993dd-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="993dd-116">mapToWindows</span></span>|<span data-ttu-id="993dd-117">トークン ハンドラーが、入力方向の UPN 要求を使用して、検証トークンを Windows アカウントにマップする必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="993dd-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="993dd-118">既定値は"false"です。</span><span class="sxs-lookup"><span data-stu-id="993dd-118">The default is "false".</span></span>|  
|<span data-ttu-id="993dd-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="993dd-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="993dd-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 証明書を使用する失効モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="993dd-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="993dd-121">既定値は、"Online"です。</span><span class="sxs-lookup"><span data-stu-id="993dd-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="993dd-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="993dd-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="993dd-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 証明書を使用する検証モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="993dd-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="993dd-124">既定値は、"PeerOrChainTrust"です。</span><span class="sxs-lookup"><span data-stu-id="993dd-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="993dd-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="993dd-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="993dd-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 証明書ストアを指定する値。</span><span class="sxs-lookup"><span data-stu-id="993dd-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="993dd-127">既定値は、"LocalMachine"です。</span><span class="sxs-lookup"><span data-stu-id="993dd-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="993dd-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="993dd-128">issuerCertificateValidator</span></span>|<span data-ttu-id="993dd-129">派生するカスタム型<xref:System.IdentityModel.Selectors.X509CertificateValidator>です。</span><span class="sxs-lookup"><span data-stu-id="993dd-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="993dd-130">場合、`issuerCertificateValidationMode`属性が"Custom"は、この型のインスタンスが発行者証明書の検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="993dd-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="993dd-131">子要素</span><span class="sxs-lookup"><span data-stu-id="993dd-131">Child Elements</span></span>  
  
|<span data-ttu-id="993dd-132">要素</span><span class="sxs-lookup"><span data-stu-id="993dd-132">Element</span></span>|<span data-ttu-id="993dd-133">説明</span><span class="sxs-lookup"><span data-stu-id="993dd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="993dd-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="993dd-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="993dd-135">指定するクレームの種類を設定、<xref:System.Security.Principal.IIdentity.Name%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="993dd-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="993dd-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="993dd-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="993dd-137">クレームを定義する、ロールの種類のコレクション内の要求の種類を指定<xref:System.Security.Claims.ClaimsIdentity>によって返されるオブジェクト、<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>トークン ハンドラーのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="993dd-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="993dd-138">親要素</span><span class="sxs-lookup"><span data-stu-id="993dd-138">Parent Elements</span></span>  
  
|<span data-ttu-id="993dd-139">要素</span><span class="sxs-lookup"><span data-stu-id="993dd-139">Element</span></span>|<span data-ttu-id="993dd-140">説明</span><span class="sxs-lookup"><span data-stu-id="993dd-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="993dd-141">\<add></span><span class="sxs-lookup"><span data-stu-id="993dd-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="993dd-142">トークン ハンドラー コレクションに指定されたセキュリティ トークン ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="993dd-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="993dd-143">コメント</span><span class="sxs-lookup"><span data-stu-id="993dd-143">Remarks</span></span>  
 <span data-ttu-id="993dd-144">`<samlSecurityTokenRequirement>`要素として表されます、<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>オブジェクト モデルのクラスし、構成に使用、`SamlSecurityTokenRequirement`プロパティを<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>または<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>です。</span><span class="sxs-lookup"><span data-stu-id="993dd-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="993dd-145">例</span><span class="sxs-lookup"><span data-stu-id="993dd-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
