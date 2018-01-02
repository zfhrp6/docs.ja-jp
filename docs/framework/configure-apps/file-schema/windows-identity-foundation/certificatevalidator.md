---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 98112b3f13ff0b8e4be50f158ce40b048b213248
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="4d316-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="4d316-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="4d316-103">証明書検証のカスタム型を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d316-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="4d316-104">場合にのみ、この型が使用される、`certificateValidationMode`の属性、 [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)要素が"Custom"に設定します。</span><span class="sxs-lookup"><span data-stu-id="4d316-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="4d316-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="4d316-105">\<system.identityModel></span></span>  
<span data-ttu-id="4d316-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4d316-106">\<identityConfiguration></span></span>  
<span data-ttu-id="4d316-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="4d316-107">\<certificateValidation></span></span>  
<span data-ttu-id="4d316-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="4d316-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d316-109">構文</span><span class="sxs-lookup"><span data-stu-id="4d316-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d316-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4d316-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4d316-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d316-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d316-112">属性</span><span class="sxs-lookup"><span data-stu-id="4d316-112">Attributes</span></span>  
  
|<span data-ttu-id="4d316-113">属性</span><span class="sxs-lookup"><span data-stu-id="4d316-113">Attribute</span></span>|<span data-ttu-id="4d316-114">説明</span><span class="sxs-lookup"><span data-stu-id="4d316-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d316-115">型</span><span class="sxs-lookup"><span data-stu-id="4d316-115">type</span></span>|<span data-ttu-id="4d316-116">派生するカスタム型を指定します、<xref:System.IdentityModel.Selectors.X509CertificateValidator>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4d316-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="4d316-117">設定、`certificateValidationMode`の属性、 [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)要素をこの型を使用するには、"Custom"にします。</span><span class="sxs-lookup"><span data-stu-id="4d316-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="4d316-118">指定する方法について、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="4d316-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="4d316-119">任意。</span><span class="sxs-lookup"><span data-stu-id="4d316-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d316-120">子要素</span><span class="sxs-lookup"><span data-stu-id="4d316-120">Child Elements</span></span>  
 <span data-ttu-id="4d316-121">なし</span><span class="sxs-lookup"><span data-stu-id="4d316-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d316-122">親要素</span><span class="sxs-lookup"><span data-stu-id="4d316-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4d316-123">要素</span><span class="sxs-lookup"><span data-stu-id="4d316-123">Element</span></span>|<span data-ttu-id="4d316-124">説明</span><span class="sxs-lookup"><span data-stu-id="4d316-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d316-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="4d316-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="4d316-126">トークン ハンドラーを使用して証明書の検証の設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="4d316-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4d316-127">例</span><span class="sxs-lookup"><span data-stu-id="4d316-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
