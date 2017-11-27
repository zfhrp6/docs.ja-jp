---
title: '&lt;claimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c4ee8833578b082f25c427b13d77072d1954197f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="88096-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="88096-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="88096-103">受信セキュリティ トークンの 1 つの省略可能または必須のクレームを指定します。</span><span class="sxs-lookup"><span data-stu-id="88096-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="88096-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="88096-104">\<system.identityModel></span></span>  
<span data-ttu-id="88096-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="88096-105">\<identityConfiguration></span></span>  
<span data-ttu-id="88096-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="88096-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="88096-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="88096-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88096-108">構文</span><span class="sxs-lookup"><span data-stu-id="88096-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88096-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="88096-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88096-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="88096-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88096-111">属性</span><span class="sxs-lookup"><span data-stu-id="88096-111">Attributes</span></span>  
  
|<span data-ttu-id="88096-112">属性</span><span class="sxs-lookup"><span data-stu-id="88096-112">Attribute</span></span>|<span data-ttu-id="88096-113">説明</span><span class="sxs-lookup"><span data-stu-id="88096-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88096-114">型</span><span class="sxs-lookup"><span data-stu-id="88096-114">type</span></span>|<span data-ttu-id="88096-115">クレームの種類。</span><span class="sxs-lookup"><span data-stu-id="88096-115">The claim type.</span></span> <span data-ttu-id="88096-116">通常は URI です。</span><span class="sxs-lookup"><span data-stu-id="88096-116">Typically a URI.</span></span> <span data-ttu-id="88096-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="88096-117">Required.</span></span>|  
|<span data-ttu-id="88096-118">optional</span><span class="sxs-lookup"><span data-stu-id="88096-118">optional</span></span>|<span data-ttu-id="88096-119">要求の種類は省略可能かどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="88096-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="88096-120">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="88096-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88096-121">子要素</span><span class="sxs-lookup"><span data-stu-id="88096-121">Child Elements</span></span>  
 <span data-ttu-id="88096-122">なし</span><span class="sxs-lookup"><span data-stu-id="88096-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88096-123">親要素</span><span class="sxs-lookup"><span data-stu-id="88096-123">Parent Elements</span></span>  
  
|<span data-ttu-id="88096-124">要素</span><span class="sxs-lookup"><span data-stu-id="88096-124">Element</span></span>|<span data-ttu-id="88096-125">説明</span><span class="sxs-lookup"><span data-stu-id="88096-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88096-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="88096-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="88096-127">必要な受信セキュリティ トークンのクレームのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="88096-127">Specifies the set of required claims for incoming security tokens.</span></span>|
