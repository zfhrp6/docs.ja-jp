---
title: '&lt;サービス&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 789fc52f628174ef61a9c7169cb0cae0f1ba8e31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicesgt"></a><span data-ttu-id="e502e-102">&lt;サービス&gt;</span><span class="sxs-lookup"><span data-stu-id="e502e-102">&lt;services&gt;</span></span>
<span data-ttu-id="e502e-103">サービスは、設定ファイルの `services` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="e502e-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e502e-104">各サービスには、独自の `service` 設定セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="e502e-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="e502e-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e502e-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e502e-106">構文</span><span class="sxs-lookup"><span data-stu-id="e502e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e502e-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e502e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e502e-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e502e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e502e-109">属性</span><span class="sxs-lookup"><span data-stu-id="e502e-109">Attributes</span></span>  
 <span data-ttu-id="e502e-110">なし</span><span class="sxs-lookup"><span data-stu-id="e502e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e502e-111">子要素</span><span class="sxs-lookup"><span data-stu-id="e502e-111">Child Elements</span></span>  
  
|<span data-ttu-id="e502e-112">要素</span><span class="sxs-lookup"><span data-stu-id="e502e-112">Element</span></span>|<span data-ttu-id="e502e-113">説明</span><span class="sxs-lookup"><span data-stu-id="e502e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e502e-114">\<service></span><span class="sxs-lookup"><span data-stu-id="e502e-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="e502e-115">サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="e502e-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e502e-116">親要素</span><span class="sxs-lookup"><span data-stu-id="e502e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e502e-117">要素</span><span class="sxs-lookup"><span data-stu-id="e502e-117">Element</span></span>|<span data-ttu-id="e502e-118">説明</span><span class="sxs-lookup"><span data-stu-id="e502e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e502e-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e502e-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e502e-120">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e502e-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e502e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e502e-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
