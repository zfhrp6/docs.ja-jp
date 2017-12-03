---
title: "&lt;ホスト&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d498190e7d7c3a6e879c50324e3b973f0f8e8fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lthostgt"></a><span data-ttu-id="06565-102">&lt;ホスト&gt;</span><span class="sxs-lookup"><span data-stu-id="06565-102">&lt;host&gt;</span></span>
<span data-ttu-id="06565-103">サービス ホストの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="06565-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="06565-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="06565-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06565-105">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="06565-105">\<services></span></span>  
<span data-ttu-id="06565-106">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="06565-106">\<service></span></span>  
<span data-ttu-id="06565-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="06565-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06565-108">構文</span><span class="sxs-lookup"><span data-stu-id="06565-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="06565-109">型</span><span class="sxs-lookup"><span data-stu-id="06565-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06565-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="06565-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06565-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="06565-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06565-112">属性</span><span class="sxs-lookup"><span data-stu-id="06565-112">Attributes</span></span>  
 <span data-ttu-id="06565-113">なし。</span><span class="sxs-lookup"><span data-stu-id="06565-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06565-114">子要素</span><span class="sxs-lookup"><span data-stu-id="06565-114">Child Elements</span></span>  
  
|<span data-ttu-id="06565-115">要素</span><span class="sxs-lookup"><span data-stu-id="06565-115">Element</span></span>|<span data-ttu-id="06565-116">説明</span><span class="sxs-lookup"><span data-stu-id="06565-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06565-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="06565-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="06565-118">サービス ホストによって使用されるベース アドレスを指定する `baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="06565-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="06565-119">\<タイムアウト ></span><span class="sxs-lookup"><span data-stu-id="06565-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="06565-120">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="06565-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06565-121">親要素</span><span class="sxs-lookup"><span data-stu-id="06565-121">Parent Elements</span></span>  
  
|<span data-ttu-id="06565-122">要素</span><span class="sxs-lookup"><span data-stu-id="06565-122">Element</span></span>|<span data-ttu-id="06565-123">説明</span><span class="sxs-lookup"><span data-stu-id="06565-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06565-124">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="06565-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="06565-125">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="06565-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06565-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="06565-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="06565-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="06565-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
