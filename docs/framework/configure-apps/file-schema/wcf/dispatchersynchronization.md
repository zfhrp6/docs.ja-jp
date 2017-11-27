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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24ae6dbf0fb67b5755aca848ea7fce6abda14b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="be221-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="be221-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="be221-103">サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="be221-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="be221-104">\<system.serviceModel >\<動作 > \<endpointBehaviors >\<動作 ></span><span class="sxs-lookup"><span data-stu-id="be221-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="be221-105">構文</span><span class="sxs-lookup"><span data-stu-id="be221-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="be221-106">型</span><span class="sxs-lookup"><span data-stu-id="be221-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="be221-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="be221-107">Attributes and elements</span></span>

<span data-ttu-id="be221-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="be221-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="be221-109">属性</span><span class="sxs-lookup"><span data-stu-id="be221-109">Attributes</span></span>

| <span data-ttu-id="be221-110">属性</span><span class="sxs-lookup"><span data-stu-id="be221-110">Attribute</span></span>               | <span data-ttu-id="be221-111">説明</span><span class="sxs-lookup"><span data-stu-id="be221-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="be221-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="be221-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="be221-113">非同期の送信動作が有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="be221-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="be221-114">チャネルで発行可能な同時受信の数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="be221-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="be221-115">この値は、サービス調整の動作を適切に構成した後に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be221-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="be221-116">子要素</span><span class="sxs-lookup"><span data-stu-id="be221-116">Child elements</span></span>

<span data-ttu-id="be221-117">なし。</span><span class="sxs-lookup"><span data-stu-id="be221-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="be221-118">親要素</span><span class="sxs-lookup"><span data-stu-id="be221-118">Parent elements</span></span>

| <span data-ttu-id="be221-119">要素</span><span class="sxs-lookup"><span data-stu-id="be221-119">Element</span></span> | <span data-ttu-id="be221-120">説明</span><span class="sxs-lookup"><span data-stu-id="be221-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="be221-121">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="be221-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="be221-122">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="be221-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="be221-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="be221-123">See also</span></span>

 <span data-ttu-id="be221-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="be221-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
