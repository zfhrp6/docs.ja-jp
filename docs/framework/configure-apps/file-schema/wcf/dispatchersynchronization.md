---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 34c12a05ee363df6b6cfc9ff3809bab50ee8d522
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747578"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="d84df-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="d84df-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="d84df-103">サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="d84df-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="d84df-104">\<system.serviceModel >\<動作 > \<endpointBehaviors >\<動作 ></span><span class="sxs-lookup"><span data-stu-id="d84df-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="d84df-105">構文</span><span class="sxs-lookup"><span data-stu-id="d84df-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="d84df-106">型</span><span class="sxs-lookup"><span data-stu-id="d84df-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="d84df-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="d84df-107">Attributes and elements</span></span>

<span data-ttu-id="d84df-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d84df-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d84df-109">属性</span><span class="sxs-lookup"><span data-stu-id="d84df-109">Attributes</span></span>

| <span data-ttu-id="d84df-110">属性</span><span class="sxs-lookup"><span data-stu-id="d84df-110">Attribute</span></span>               | <span data-ttu-id="d84df-111">説明</span><span class="sxs-lookup"><span data-stu-id="d84df-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="d84df-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="d84df-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="d84df-113">非同期の送信動作が有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="d84df-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="d84df-114">チャネルで発行可能な同時受信の数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="d84df-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="d84df-115">この値は、サービス調整の動作を適切に構成した後に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84df-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="d84df-116">子要素</span><span class="sxs-lookup"><span data-stu-id="d84df-116">Child elements</span></span>

<span data-ttu-id="d84df-117">なし。</span><span class="sxs-lookup"><span data-stu-id="d84df-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d84df-118">親要素</span><span class="sxs-lookup"><span data-stu-id="d84df-118">Parent elements</span></span>

| <span data-ttu-id="d84df-119">要素</span><span class="sxs-lookup"><span data-stu-id="d84df-119">Element</span></span> | <span data-ttu-id="d84df-120">説明</span><span class="sxs-lookup"><span data-stu-id="d84df-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="d84df-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d84df-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d84df-122">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="d84df-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d84df-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d84df-123">See also</span></span>

 <span data-ttu-id="d84df-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="d84df-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
