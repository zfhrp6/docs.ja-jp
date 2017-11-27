---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 177639b973bf8c597bc8b994d37c99647c72feb8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="aafc9-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="aafc9-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="aafc9-103">暗号化し、トークン暗号化解除に使用される X.509 証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="aafc9-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="aafc9-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="aafc9-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="aafc9-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="aafc9-105">\<federationConfiguration></span></span>  
<span data-ttu-id="aafc9-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="aafc9-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aafc9-107">構文</span><span class="sxs-lookup"><span data-stu-id="aafc9-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aafc9-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="aafc9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aafc9-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="aafc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aafc9-110">属性</span><span class="sxs-lookup"><span data-stu-id="aafc9-110">Attributes</span></span>  
 <span data-ttu-id="aafc9-111">なし</span><span class="sxs-lookup"><span data-stu-id="aafc9-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aafc9-112">子要素</span><span class="sxs-lookup"><span data-stu-id="aafc9-112">Child Elements</span></span>  
  
|<span data-ttu-id="aafc9-113">要素</span><span class="sxs-lookup"><span data-stu-id="aafc9-113">Element</span></span>|<span data-ttu-id="aafc9-114">説明</span><span class="sxs-lookup"><span data-stu-id="aafc9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aafc9-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="aafc9-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="aafc9-116">検索し、証明書ストアで X.509 証明書の検証に使用される設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="aafc9-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aafc9-117">親要素</span><span class="sxs-lookup"><span data-stu-id="aafc9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="aafc9-118">要素</span><span class="sxs-lookup"><span data-stu-id="aafc9-118">Element</span></span>|<span data-ttu-id="aafc9-119">説明</span><span class="sxs-lookup"><span data-stu-id="aafc9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aafc9-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="aafc9-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="aafc9-121">構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="aafc9-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aafc9-122">例</span><span class="sxs-lookup"><span data-stu-id="aafc9-122">Example</span></span>  
 <span data-ttu-id="aafc9-123">次の XML の使用方法を示します、 \<serviceCertificate > 要素。</span><span class="sxs-lookup"><span data-stu-id="aafc9-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="aafc9-124">XML を取得、`CustomToken`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="aafc9-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
