---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af59562dbf6c13970526f1665a9ba2c57c4f32ee
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="a1208-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="a1208-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="a1208-103">暗号化し、トークン暗号化解除に使用される X.509 証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="a1208-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="a1208-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="a1208-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="a1208-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a1208-105">\<federationConfiguration></span></span>  
<span data-ttu-id="a1208-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="a1208-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1208-107">構文</span><span class="sxs-lookup"><span data-stu-id="a1208-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1208-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a1208-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a1208-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1208-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1208-110">属性</span><span class="sxs-lookup"><span data-stu-id="a1208-110">Attributes</span></span>  
 <span data-ttu-id="a1208-111">なし</span><span class="sxs-lookup"><span data-stu-id="a1208-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1208-112">子要素</span><span class="sxs-lookup"><span data-stu-id="a1208-112">Child Elements</span></span>  
  
|<span data-ttu-id="a1208-113">要素</span><span class="sxs-lookup"><span data-stu-id="a1208-113">Element</span></span>|<span data-ttu-id="a1208-114">説明</span><span class="sxs-lookup"><span data-stu-id="a1208-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1208-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="a1208-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="a1208-116">検索し、証明書ストアで X.509 証明書の検証に使用される設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1208-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1208-117">親要素</span><span class="sxs-lookup"><span data-stu-id="a1208-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a1208-118">要素</span><span class="sxs-lookup"><span data-stu-id="a1208-118">Element</span></span>|<span data-ttu-id="a1208-119">説明</span><span class="sxs-lookup"><span data-stu-id="a1208-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1208-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="a1208-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="a1208-121">構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="a1208-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1208-122">例</span><span class="sxs-lookup"><span data-stu-id="a1208-122">Example</span></span>  
 <span data-ttu-id="a1208-123">次の XML の使用方法を示します、 \<serviceCertificate > 要素。</span><span class="sxs-lookup"><span data-stu-id="a1208-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="a1208-124">XML を取得、`CustomToken`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="a1208-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
