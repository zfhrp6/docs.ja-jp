---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0a6349f50c8810d834d7887daecb6ac9cffb2e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="94871-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="94871-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="94871-103">サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="94871-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="94871-104">\<system.serviceModel >\<動作 > \<endpointBehaviors >\<動作 ></span><span class="sxs-lookup"><span data-stu-id="94871-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="94871-105">構文</span><span class="sxs-lookup"><span data-stu-id="94871-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="94871-106">型</span><span class="sxs-lookup"><span data-stu-id="94871-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="94871-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="94871-107">Attributes and elements</span></span>

<span data-ttu-id="94871-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="94871-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="94871-109">属性</span><span class="sxs-lookup"><span data-stu-id="94871-109">Attributes</span></span>

| <span data-ttu-id="94871-110">属性</span><span class="sxs-lookup"><span data-stu-id="94871-110">Attribute</span></span>               | <span data-ttu-id="94871-111">説明</span><span class="sxs-lookup"><span data-stu-id="94871-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="94871-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="94871-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="94871-113">非同期の送信動作が有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="94871-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="94871-114">チャネルで発行可能な同時受信の数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="94871-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="94871-115">この値は、サービス調整の動作を適切に構成した後に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94871-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="94871-116">子要素</span><span class="sxs-lookup"><span data-stu-id="94871-116">Child elements</span></span>

<span data-ttu-id="94871-117">なし。</span><span class="sxs-lookup"><span data-stu-id="94871-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94871-118">親要素</span><span class="sxs-lookup"><span data-stu-id="94871-118">Parent elements</span></span>

| <span data-ttu-id="94871-119">要素</span><span class="sxs-lookup"><span data-stu-id="94871-119">Element</span></span> | <span data-ttu-id="94871-120">説明</span><span class="sxs-lookup"><span data-stu-id="94871-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="94871-121">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="94871-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="94871-122">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="94871-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="94871-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="94871-123">See also</span></span>

 <span data-ttu-id="94871-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="94871-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
