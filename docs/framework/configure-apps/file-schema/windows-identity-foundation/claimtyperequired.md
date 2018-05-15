---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6fb600aac46b3ee5cb54fa904d35ac7b7ed90719
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="4d7ed-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="4d7ed-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="4d7ed-103">必要な受信セキュリティ トークンのクレームのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d7ed-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="4d7ed-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4d7ed-104">\<system.identityModel></span></span>  
<span data-ttu-id="4d7ed-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d7ed-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4d7ed-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="4d7ed-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7ed-107">構文</span><span class="sxs-lookup"><span data-stu-id="4d7ed-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d7ed-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4d7ed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d7ed-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d7ed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d7ed-110">属性</span><span class="sxs-lookup"><span data-stu-id="4d7ed-110">Attributes</span></span>  
 <span data-ttu-id="4d7ed-111">なし</span><span class="sxs-lookup"><span data-stu-id="4d7ed-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d7ed-112">子要素</span><span class="sxs-lookup"><span data-stu-id="4d7ed-112">Child Elements</span></span>  
  
|<span data-ttu-id="4d7ed-113">要素</span><span class="sxs-lookup"><span data-stu-id="4d7ed-113">Element</span></span>|<span data-ttu-id="4d7ed-114">説明</span><span class="sxs-lookup"><span data-stu-id="4d7ed-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d7ed-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="4d7ed-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="4d7ed-116">受信セキュリティ トークンの 1 つの省略可能または必須のクレームを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d7ed-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d7ed-117">親要素</span><span class="sxs-lookup"><span data-stu-id="4d7ed-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4d7ed-118">要素</span><span class="sxs-lookup"><span data-stu-id="4d7ed-118">Element</span></span>|<span data-ttu-id="4d7ed-119">説明</span><span class="sxs-lookup"><span data-stu-id="4d7ed-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d7ed-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4d7ed-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4d7ed-121">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d7ed-121">Specifies service-level identity settings.</span></span>|
