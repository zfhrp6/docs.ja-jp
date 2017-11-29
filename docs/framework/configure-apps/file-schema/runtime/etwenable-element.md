---
title: "&lt;etwEnable&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b36c52338754df0f4fd3c963848e36afeb140501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="a3dd3-102">&lt;etwEnable&gt;要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="a3dd3-103">共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="a3dd3-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-104">\<configuration> Element</span></span>  
<span data-ttu-id="a3dd3-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-105">\<runtime> Element</span></span>  
<span data-ttu-id="a3dd3-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="a3dd3-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3dd3-107">構文</span><span class="sxs-lookup"><span data-stu-id="a3dd3-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3dd3-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3dd3-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3dd3-110">属性</span><span class="sxs-lookup"><span data-stu-id="a3dd3-110">Attributes</span></span>  
  
|<span data-ttu-id="a3dd3-111">属性</span><span class="sxs-lookup"><span data-stu-id="a3dd3-111">Attribute</span></span>|<span data-ttu-id="a3dd3-112">説明</span><span class="sxs-lookup"><span data-stu-id="a3dd3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3dd3-113">enabled</span><span class="sxs-lookup"><span data-stu-id="a3dd3-113">enabled</span></span>|<span data-ttu-id="a3dd3-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3dd3-115">ETW を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a3dd3-116">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="a3dd3-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="a3dd3-117">値</span><span class="sxs-lookup"><span data-stu-id="a3dd3-117">Value</span></span>|<span data-ttu-id="a3dd3-118">説明</span><span class="sxs-lookup"><span data-stu-id="a3dd3-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a3dd3-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="a3dd3-119">true</span></span>|<span data-ttu-id="a3dd3-120">ETW を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-120">Enable ETW.</span></span> <span data-ttu-id="a3dd3-121">これは、以降、Windows Vista および Windows Server 2008 オペレーティング システムの Windows のバージョンの既定値です。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="a3dd3-122">False</span><span class="sxs-lookup"><span data-stu-id="a3dd3-122">false</span></span>|<span data-ttu-id="a3dd3-123">ETW を無効にします。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-123">Disable ETW.</span></span> <span data-ttu-id="a3dd3-124">これは、以前のバージョンの Windows の既定値です。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3dd3-125">子要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-125">Child Elements</span></span>  
 <span data-ttu-id="a3dd3-126">なし。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3dd3-127">親要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a3dd3-128">要素</span><span class="sxs-lookup"><span data-stu-id="a3dd3-128">Element</span></span>|<span data-ttu-id="a3dd3-129">説明</span><span class="sxs-lookup"><span data-stu-id="a3dd3-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a3dd3-130">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a3dd3-131">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3dd3-132">コメント</span><span class="sxs-lookup"><span data-stu-id="a3dd3-132">Remarks</span></span>  
 <span data-ttu-id="a3dd3-133">Windows Vista 以降では、ETW は既定で有効にします。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="a3dd3-134">アプリケーションの ETW を無効にするのにには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="a3dd3-135">以前のバージョンの Windows では、この要素を使用して、アプリケーションの ETW を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dd3-136">ETW を有効になっているか、レジストリ設定を使用して、サーバーでグローバルに無効にします。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="a3dd3-137">参照してください[.NET Framework のログ記録を制御する](../../../../../docs/framework/performance/controlling-logging.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3dd3-138">例</span><span class="sxs-lookup"><span data-stu-id="a3dd3-138">Example</span></span>  
 <span data-ttu-id="a3dd3-139">次の例では、アプリケーションの ETW トレースを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a3dd3-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3dd3-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3dd3-140">See Also</span></span>  
 [<span data-ttu-id="a3dd3-141">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a3dd3-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a3dd3-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="a3dd3-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a3dd3-143">.NET Framework のログ記録の制御</span><span class="sxs-lookup"><span data-stu-id="a3dd3-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
