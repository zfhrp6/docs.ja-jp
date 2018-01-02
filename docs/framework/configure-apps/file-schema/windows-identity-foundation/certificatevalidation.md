---
title: '&lt;certificateValidation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7a5d31bce5f71e644b40b3aa7e7c0c1c8790cab6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="1ba70-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="1ba70-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="1ba70-103">トークン ハンドラーを使用して証明書の検証の設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="1ba70-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="1ba70-104">特定のハンドラーが、独自の検証コントロールで構成されている場合、これらの設定は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="1ba70-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="1ba70-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="1ba70-105">\<system.identityModel></span></span>  
<span data-ttu-id="1ba70-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1ba70-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1ba70-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="1ba70-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ba70-108">構文</span><span class="sxs-lookup"><span data-stu-id="1ba70-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ba70-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1ba70-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1ba70-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1ba70-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ba70-111">属性</span><span class="sxs-lookup"><span data-stu-id="1ba70-111">Attributes</span></span>  
  
|<span data-ttu-id="1ba70-112">属性</span><span class="sxs-lookup"><span data-stu-id="1ba70-112">Attribute</span></span>|<span data-ttu-id="1ba70-113">説明</span><span class="sxs-lookup"><span data-stu-id="1ba70-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ba70-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1ba70-114">certificateValidationMode</span></span>|<span data-ttu-id="1ba70-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 証明書を使用する検証モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="1ba70-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1ba70-116">既定値は、"PeerOrChainTrust"です。</span><span class="sxs-lookup"><span data-stu-id="1ba70-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="1ba70-117">カスタム検証を指定する"Custom"には、この属性を設定しを使用して検証を指定、 [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)要素。</span><span class="sxs-lookup"><span data-stu-id="1ba70-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="1ba70-118">任意。</span><span class="sxs-lookup"><span data-stu-id="1ba70-118">Optional.</span></span>|  
|<span data-ttu-id="1ba70-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="1ba70-119">revocationMode</span></span>|<span data-ttu-id="1ba70-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 証明書を使用する失効モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="1ba70-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1ba70-121">既定値は、"Online"です。</span><span class="sxs-lookup"><span data-stu-id="1ba70-121">The default value is "Online".</span></span> <span data-ttu-id="1ba70-122">任意。</span><span class="sxs-lookup"><span data-stu-id="1ba70-122">Optional.</span></span>|  
|<span data-ttu-id="1ba70-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1ba70-123">trustedStoreLocation</span></span>|<span data-ttu-id="1ba70-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 証明書ストアを指定する値。</span><span class="sxs-lookup"><span data-stu-id="1ba70-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1ba70-125">既定値は、"LocalMachine"です。</span><span class="sxs-lookup"><span data-stu-id="1ba70-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="1ba70-126">任意。</span><span class="sxs-lookup"><span data-stu-id="1ba70-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ba70-127">子要素</span><span class="sxs-lookup"><span data-stu-id="1ba70-127">Child Elements</span></span>  
  
|<span data-ttu-id="1ba70-128">要素</span><span class="sxs-lookup"><span data-stu-id="1ba70-128">Element</span></span>|<span data-ttu-id="1ba70-129">説明</span><span class="sxs-lookup"><span data-stu-id="1ba70-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ba70-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="1ba70-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="1ba70-131">証明書検証のカスタム型を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ba70-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1ba70-132">場合にのみ、この型が使用される、`certificateValidationMode`の属性、 [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)要素が"Custom"に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ba70-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ba70-133">親要素</span><span class="sxs-lookup"><span data-stu-id="1ba70-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1ba70-134">要素</span><span class="sxs-lookup"><span data-stu-id="1ba70-134">Element</span></span>|<span data-ttu-id="1ba70-135">説明</span><span class="sxs-lookup"><span data-stu-id="1ba70-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ba70-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1ba70-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="1ba70-137">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ba70-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1ba70-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1ba70-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1ba70-139">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ba70-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ba70-140">コメント</span><span class="sxs-lookup"><span data-stu-id="1ba70-140">Remarks</span></span>  
 <span data-ttu-id="1ba70-141">A`<certificateValidation>`下にあるサービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラーのコレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="1ba70-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1ba70-142">サービスに指定されたトークン ハンドラーはコレクションの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="1ba70-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="1ba70-143">いくつかのトークン ハンドラーを使用すると、構成で証明書検証の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1ba70-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="1ba70-144">個々 のトークン ハンドラーの設定は、サービス レベルとセキュリティ トークン ハンドラーのコレクションの両方に指定された上書きします。</span><span class="sxs-lookup"><span data-stu-id="1ba70-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ba70-145">例</span><span class="sxs-lookup"><span data-stu-id="1ba70-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
