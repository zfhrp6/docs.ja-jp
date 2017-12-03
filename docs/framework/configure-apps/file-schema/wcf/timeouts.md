---
title: "&lt;タイムアウト&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da80ab797078e1fe912ccbfff07d7fb2da49664e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="dffe8-102">&lt;タイムアウト&gt;</span><span class="sxs-lookup"><span data-stu-id="dffe8-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="dffe8-103">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="dffe8-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="dffe8-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dffe8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dffe8-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="dffe8-105">\<client></span></span>  
<span data-ttu-id="dffe8-106">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="dffe8-106">\<endpoint></span></span>  
<span data-ttu-id="dffe8-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="dffe8-107">\<host></span></span>  
<span data-ttu-id="dffe8-108">\<タイムアウト ></span><span class="sxs-lookup"><span data-stu-id="dffe8-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffe8-109">構文</span><span class="sxs-lookup"><span data-stu-id="dffe8-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dffe8-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dffe8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dffe8-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dffe8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dffe8-112">属性</span><span class="sxs-lookup"><span data-stu-id="dffe8-112">Attributes</span></span>  
  
|<span data-ttu-id="dffe8-113">属性</span><span class="sxs-lookup"><span data-stu-id="dffe8-113">Attribute</span></span>|<span data-ttu-id="dffe8-114">説明</span><span class="sxs-lookup"><span data-stu-id="dffe8-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="dffe8-115">サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="dffe8-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="dffe8-116">サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="dffe8-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dffe8-117">子要素</span><span class="sxs-lookup"><span data-stu-id="dffe8-117">Child Elements</span></span>  
 <span data-ttu-id="dffe8-118">なし。</span><span class="sxs-lookup"><span data-stu-id="dffe8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dffe8-119">親要素</span><span class="sxs-lookup"><span data-stu-id="dffe8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dffe8-120">要素</span><span class="sxs-lookup"><span data-stu-id="dffe8-120">Element</span></span>|<span data-ttu-id="dffe8-121">説明</span><span class="sxs-lookup"><span data-stu-id="dffe8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dffe8-122">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="dffe8-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="dffe8-123">サービス ホストの設定を指定する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="dffe8-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dffe8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="dffe8-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="dffe8-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="dffe8-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
