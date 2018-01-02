---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="b7a73-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="b7a73-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="b7a73-103">必要な受信セキュリティ トークンのクレームのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7a73-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="b7a73-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b7a73-104">\<system.identityModel></span></span>  
<span data-ttu-id="b7a73-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b7a73-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b7a73-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="b7a73-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a73-107">構文</span><span class="sxs-lookup"><span data-stu-id="b7a73-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7a73-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b7a73-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b7a73-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7a73-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7a73-110">属性</span><span class="sxs-lookup"><span data-stu-id="b7a73-110">Attributes</span></span>  
 <span data-ttu-id="b7a73-111">なし</span><span class="sxs-lookup"><span data-stu-id="b7a73-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7a73-112">子要素</span><span class="sxs-lookup"><span data-stu-id="b7a73-112">Child Elements</span></span>  
  
|<span data-ttu-id="b7a73-113">要素</span><span class="sxs-lookup"><span data-stu-id="b7a73-113">Element</span></span>|<span data-ttu-id="b7a73-114">説明</span><span class="sxs-lookup"><span data-stu-id="b7a73-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a73-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="b7a73-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="b7a73-116">受信セキュリティ トークンの 1 つの省略可能または必須のクレームを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7a73-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7a73-117">親要素</span><span class="sxs-lookup"><span data-stu-id="b7a73-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b7a73-118">要素</span><span class="sxs-lookup"><span data-stu-id="b7a73-118">Element</span></span>|<span data-ttu-id="b7a73-119">説明</span><span class="sxs-lookup"><span data-stu-id="b7a73-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a73-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b7a73-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="b7a73-121">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7a73-121">Specifies service-level identity settings.</span></span>|
