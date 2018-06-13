---
title: '&lt;ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94f8586a9ca63b8c1f1128cdda4a74ccfe0f5416
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767428"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="b3bd9-102">&lt;ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="b3bd9-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="b3bd9-103">受信セキュリティ トークンの 1 つの省略可能または必須のクレームを指定します。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="b3bd9-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b3bd9-104">\<system.identityModel></span></span>  
<span data-ttu-id="b3bd9-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b3bd9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b3bd9-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="b3bd9-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="b3bd9-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="b3bd9-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3bd9-108">構文</span><span class="sxs-lookup"><span data-stu-id="b3bd9-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3bd9-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b3bd9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b3bd9-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3bd9-111">属性</span><span class="sxs-lookup"><span data-stu-id="b3bd9-111">Attributes</span></span>  
  
|<span data-ttu-id="b3bd9-112">属性</span><span class="sxs-lookup"><span data-stu-id="b3bd9-112">Attribute</span></span>|<span data-ttu-id="b3bd9-113">説明</span><span class="sxs-lookup"><span data-stu-id="b3bd9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3bd9-114">型</span><span class="sxs-lookup"><span data-stu-id="b3bd9-114">type</span></span>|<span data-ttu-id="b3bd9-115">要求の種類。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-115">The claim type.</span></span> <span data-ttu-id="b3bd9-116">通常は URI です。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-116">Typically a URI.</span></span> <span data-ttu-id="b3bd9-117">必須。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-117">Required.</span></span>|  
|<span data-ttu-id="b3bd9-118">optional</span><span class="sxs-lookup"><span data-stu-id="b3bd9-118">optional</span></span>|<span data-ttu-id="b3bd9-119">要求の種類は省略可能かどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="b3bd9-120">任意。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3bd9-121">子要素</span><span class="sxs-lookup"><span data-stu-id="b3bd9-121">Child Elements</span></span>  
 <span data-ttu-id="b3bd9-122">なし</span><span class="sxs-lookup"><span data-stu-id="b3bd9-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3bd9-123">親要素</span><span class="sxs-lookup"><span data-stu-id="b3bd9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b3bd9-124">要素</span><span class="sxs-lookup"><span data-stu-id="b3bd9-124">Element</span></span>|<span data-ttu-id="b3bd9-125">説明</span><span class="sxs-lookup"><span data-stu-id="b3bd9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3bd9-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="b3bd9-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="b3bd9-127">必要な受信セキュリティ トークンのクレームのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b3bd9-127">Specifies the set of required claims for incoming security tokens.</span></span>|
