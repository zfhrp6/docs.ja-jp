---
title: '&lt;ホスト&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 9c48fff7473449192887bfd8cc201dd87cb4e7f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lthostgt"></a><span data-ttu-id="46717-102">&lt;ホスト&gt;</span><span class="sxs-lookup"><span data-stu-id="46717-102">&lt;host&gt;</span></span>
<span data-ttu-id="46717-103">サービス ホストの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="46717-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="46717-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="46717-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="46717-105">\<services></span><span class="sxs-lookup"><span data-stu-id="46717-105">\<services></span></span>  
<span data-ttu-id="46717-106">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="46717-106">\<service></span></span>  
<span data-ttu-id="46717-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="46717-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46717-108">構文</span><span class="sxs-lookup"><span data-stu-id="46717-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="46717-109">型</span><span class="sxs-lookup"><span data-stu-id="46717-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46717-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="46717-110">Attributes and Elements</span></span>  
 <span data-ttu-id="46717-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="46717-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46717-112">属性</span><span class="sxs-lookup"><span data-stu-id="46717-112">Attributes</span></span>  
 <span data-ttu-id="46717-113">なし。</span><span class="sxs-lookup"><span data-stu-id="46717-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46717-114">子要素</span><span class="sxs-lookup"><span data-stu-id="46717-114">Child Elements</span></span>  
  
|<span data-ttu-id="46717-115">要素</span><span class="sxs-lookup"><span data-stu-id="46717-115">Element</span></span>|<span data-ttu-id="46717-116">説明</span><span class="sxs-lookup"><span data-stu-id="46717-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46717-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="46717-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="46717-118">サービス ホストによって使用されるベース アドレスを指定する `baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="46717-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="46717-119">\<タイムアウト ></span><span class="sxs-lookup"><span data-stu-id="46717-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="46717-120">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="46717-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46717-121">親要素</span><span class="sxs-lookup"><span data-stu-id="46717-121">Parent Elements</span></span>  
  
|<span data-ttu-id="46717-122">要素</span><span class="sxs-lookup"><span data-stu-id="46717-122">Element</span></span>|<span data-ttu-id="46717-123">説明</span><span class="sxs-lookup"><span data-stu-id="46717-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46717-124">\<service></span><span class="sxs-lookup"><span data-stu-id="46717-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="46717-125">Windows Communication Foundation (WCF) サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="46717-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46717-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="46717-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="46717-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="46717-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
