---
title: "&lt;サービス&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="b8d13-102">&lt;サービス&gt;</span><span class="sxs-lookup"><span data-stu-id="b8d13-102">&lt;services&gt;</span></span>
<span data-ttu-id="b8d13-103">サービスは、設定ファイルの `services` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="b8d13-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="b8d13-104">各サービスには、独自の `service` 設定セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="b8d13-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="b8d13-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b8d13-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d13-106">構文</span><span class="sxs-lookup"><span data-stu-id="b8d13-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8d13-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b8d13-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8d13-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8d13-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8d13-109">属性</span><span class="sxs-lookup"><span data-stu-id="b8d13-109">Attributes</span></span>  
 <span data-ttu-id="b8d13-110">なし</span><span class="sxs-lookup"><span data-stu-id="b8d13-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8d13-111">子要素</span><span class="sxs-lookup"><span data-stu-id="b8d13-111">Child Elements</span></span>  
  
|<span data-ttu-id="b8d13-112">要素</span><span class="sxs-lookup"><span data-stu-id="b8d13-112">Element</span></span>|<span data-ttu-id="b8d13-113">説明</span><span class="sxs-lookup"><span data-stu-id="b8d13-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8d13-114">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="b8d13-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="b8d13-115">サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8d13-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8d13-116">親要素</span><span class="sxs-lookup"><span data-stu-id="b8d13-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b8d13-117">要素</span><span class="sxs-lookup"><span data-stu-id="b8d13-117">Element</span></span>|<span data-ttu-id="b8d13-118">説明</span><span class="sxs-lookup"><span data-stu-id="b8d13-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8d13-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b8d13-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="b8d13-120">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b8d13-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8d13-121">参照</span><span class="sxs-lookup"><span data-stu-id="b8d13-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
