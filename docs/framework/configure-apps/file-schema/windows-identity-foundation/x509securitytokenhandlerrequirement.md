---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8af4a718fc9f4ba7f674d98e13424bb443693c6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="98a86-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="98a86-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="98a86-103">省略可能な構成を提供、<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>クラスまたは派生クラス。</span><span class="sxs-lookup"><span data-stu-id="98a86-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="98a86-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="98a86-104">\<system.identityModel></span></span>  
<span data-ttu-id="98a86-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="98a86-105">\<identityConfiguration></span></span>  
<span data-ttu-id="98a86-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="98a86-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="98a86-107">\<add></span><span class="sxs-lookup"><span data-stu-id="98a86-107">\<add></span></span>  
<span data-ttu-id="98a86-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="98a86-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a86-109">構文</span><span class="sxs-lookup"><span data-stu-id="98a86-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98a86-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="98a86-110">Attributes and Elements</span></span>  
 <span data-ttu-id="98a86-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="98a86-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98a86-112">属性</span><span class="sxs-lookup"><span data-stu-id="98a86-112">Attributes</span></span>  
  
|<span data-ttu-id="98a86-113">属性</span><span class="sxs-lookup"><span data-stu-id="98a86-113">Attribute</span></span>|<span data-ttu-id="98a86-114">説明</span><span class="sxs-lookup"><span data-stu-id="98a86-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98a86-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="98a86-115">certificateValidationMode</span></span>|<span data-ttu-id="98a86-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 証明書を使用する検証モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="98a86-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="98a86-117">既定値は、"PeerOrChainTrust"です。</span><span class="sxs-lookup"><span data-stu-id="98a86-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="98a86-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="98a86-118">mapToWindows</span></span>|<span data-ttu-id="98a86-119">トークン ハンドラーが、入力方向の UPN 要求を使用して、検証トークンを Windows アカウントにマップする必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="98a86-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="98a86-120">既定値は"false"です。</span><span class="sxs-lookup"><span data-stu-id="98a86-120">The default is "false".</span></span>|  
|<span data-ttu-id="98a86-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="98a86-121">revocationMode</span></span>|<span data-ttu-id="98a86-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 証明書を使用する失効モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="98a86-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="98a86-123">既定値は、"Online"です。</span><span class="sxs-lookup"><span data-stu-id="98a86-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="98a86-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="98a86-124">trustedStoreLocation</span></span>|<span data-ttu-id="98a86-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 証明書ストアを指定する値。</span><span class="sxs-lookup"><span data-stu-id="98a86-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="98a86-126">既定値は、"LocalMachine"です。</span><span class="sxs-lookup"><span data-stu-id="98a86-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="98a86-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="98a86-127">certificateValidator</span></span>|<span data-ttu-id="98a86-128">派生するカスタム型<xref:System.IdentityModel.Selectors.X509CertificateValidator>です。</span><span class="sxs-lookup"><span data-stu-id="98a86-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="98a86-129">場合、`certificateValidationMode`属性が"Custom"は、この型のインスタンスが発行者証明書の検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="98a86-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98a86-130">子要素</span><span class="sxs-lookup"><span data-stu-id="98a86-130">Child Elements</span></span>  
 <span data-ttu-id="98a86-131">なし</span><span class="sxs-lookup"><span data-stu-id="98a86-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98a86-132">親要素</span><span class="sxs-lookup"><span data-stu-id="98a86-132">Parent Elements</span></span>  
  
|<span data-ttu-id="98a86-133">要素</span><span class="sxs-lookup"><span data-stu-id="98a86-133">Element</span></span>|<span data-ttu-id="98a86-134">説明</span><span class="sxs-lookup"><span data-stu-id="98a86-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98a86-135">\<add></span><span class="sxs-lookup"><span data-stu-id="98a86-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="98a86-136">トークン ハンドラー コレクションに指定されたセキュリティ トークン ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="98a86-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="98a86-137">例</span><span class="sxs-lookup"><span data-stu-id="98a86-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
