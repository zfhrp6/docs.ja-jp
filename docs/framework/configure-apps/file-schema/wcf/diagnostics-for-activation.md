---
title: "アクティベーションの &lt;diagnostics&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 29f2e56dd18da9dc3ce3206f5c3c80f4a47a7ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="d9d18-102">アクティベーションの &lt;diagnostics&gt;</span><span class="sxs-lookup"><span data-stu-id="d9d18-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="d9d18-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] リスナーの診断機能を構成します。</span><span class="sxs-lookup"><span data-stu-id="d9d18-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="d9d18-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d9d18-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="d9d18-105">\<診断 ></span><span class="sxs-lookup"><span data-stu-id="d9d18-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d18-106">構文</span><span class="sxs-lookup"><span data-stu-id="d9d18-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="d9d18-107">型</span><span class="sxs-lookup"><span data-stu-id="d9d18-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9d18-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d9d18-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d9d18-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9d18-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9d18-110">属性</span><span class="sxs-lookup"><span data-stu-id="d9d18-110">Attributes</span></span>  
  
|<span data-ttu-id="d9d18-111">属性</span><span class="sxs-lookup"><span data-stu-id="d9d18-111">Attribute</span></span>|<span data-ttu-id="d9d18-112">説明</span><span class="sxs-lookup"><span data-stu-id="d9d18-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="d9d18-113">診断用パフォーマンス カウンターが有効であるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="d9d18-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9d18-114">子要素</span><span class="sxs-lookup"><span data-stu-id="d9d18-114">Child Elements</span></span>  
 <span data-ttu-id="d9d18-115">なし。</span><span class="sxs-lookup"><span data-stu-id="d9d18-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9d18-116">親要素</span><span class="sxs-lookup"><span data-stu-id="d9d18-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d9d18-117">要素</span><span class="sxs-lookup"><span data-stu-id="d9d18-117">Element</span></span>|<span data-ttu-id="d9d18-118">説明</span><span class="sxs-lookup"><span data-stu-id="d9d18-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9d18-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d9d18-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="d9d18-120">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9d18-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9d18-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9d18-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
