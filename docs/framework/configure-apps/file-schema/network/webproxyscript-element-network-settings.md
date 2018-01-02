---
title: "&lt;webProxyScript&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4c7d6154d354e806a04ccc9da062db64c534039b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="671f4-102">&lt;webProxyScript&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="671f4-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="671f4-103">Web プロキシを検出するためのスクリプトの特性を構成します。</span><span class="sxs-lookup"><span data-stu-id="671f4-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="671f4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="671f4-104">\<configuration></span></span>  
<span data-ttu-id="671f4-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="671f4-105">\<system.net></span></span>  
<span data-ttu-id="671f4-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="671f4-106">\<settings></span></span>  
<span data-ttu-id="671f4-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="671f4-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="671f4-108">構文</span><span class="sxs-lookup"><span data-stu-id="671f4-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="671f4-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="671f4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="671f4-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="671f4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="671f4-111">属性</span><span class="sxs-lookup"><span data-stu-id="671f4-111">Attributes</span></span>  
  
|<span data-ttu-id="671f4-112">属性</span><span class="sxs-lookup"><span data-stu-id="671f4-112">Attribute</span></span>|<span data-ttu-id="671f4-113">説明</span><span class="sxs-lookup"><span data-stu-id="671f4-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="671f4-114">時間、分、および秒でスクリプトをダウンロードする最大時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="671f4-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="671f4-115">既定値は、1 分です。</span><span class="sxs-lookup"><span data-stu-id="671f4-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="671f4-116">子要素</span><span class="sxs-lookup"><span data-stu-id="671f4-116">Child Elements</span></span>  
 <span data-ttu-id="671f4-117">なし。</span><span class="sxs-lookup"><span data-stu-id="671f4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="671f4-118">親要素</span><span class="sxs-lookup"><span data-stu-id="671f4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="671f4-119">要素</span><span class="sxs-lookup"><span data-stu-id="671f4-119">Element</span></span>|<span data-ttu-id="671f4-120">説明</span><span class="sxs-lookup"><span data-stu-id="671f4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="671f4-121">設定</span><span class="sxs-lookup"><span data-stu-id="671f4-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="671f4-122"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="671f4-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="671f4-123">コメント</span><span class="sxs-lookup"><span data-stu-id="671f4-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="671f4-124">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="671f4-124">Configuration Files</span></span>  
 <span data-ttu-id="671f4-125">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="671f4-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671f4-126">参照</span><span class="sxs-lookup"><span data-stu-id="671f4-126">See Also</span></span>  
 [<span data-ttu-id="671f4-127">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="671f4-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
