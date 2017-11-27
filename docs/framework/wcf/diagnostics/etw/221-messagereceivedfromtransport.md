---
title: 221 - MessageReceivedFromTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f977f938844f48182be6662f489506e8119fe67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="fc974-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="fc974-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="fc974-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fc974-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fc974-104">ID</span><span class="sxs-lookup"><span data-stu-id="fc974-104">ID</span></span>|<span data-ttu-id="fc974-105">221</span><span class="sxs-lookup"><span data-stu-id="fc974-105">221</span></span>|  
|<span data-ttu-id="fc974-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fc974-106">Keywords</span></span>|<span data-ttu-id="fc974-107">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fc974-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fc974-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fc974-108">Level</span></span>|<span data-ttu-id="fc974-109">情報</span><span class="sxs-lookup"><span data-stu-id="fc974-109">Information</span></span>|  
|<span data-ttu-id="fc974-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fc974-110">Channel</span></span>|<span data-ttu-id="fc974-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fc974-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fc974-112">説明</span><span class="sxs-lookup"><span data-stu-id="fc974-112">Description</span></span>  
 <span data-ttu-id="fc974-113">このイベントは、サービス モデルがトランスポートからメッセージを受信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc974-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fc974-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fc974-114">Message</span></span>  
 <span data-ttu-id="fc974-115">ディスパッチャーがトランスポートからメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="fc974-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="fc974-116">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="fc974-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fc974-117">詳細</span><span class="sxs-lookup"><span data-stu-id="fc974-117">Details</span></span>  
  
|<span data-ttu-id="fc974-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fc974-118">Data Item Name</span></span>|<span data-ttu-id="fc974-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fc974-119">Data Item Type</span></span>|<span data-ttu-id="fc974-120">説明</span><span class="sxs-lookup"><span data-stu-id="fc974-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fc974-121">Correlation ID</span><span class="sxs-lookup"><span data-stu-id="fc974-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="fc974-122">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="fc974-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="fc974-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="fc974-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="fc974-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="fc974-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fc974-125">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="fc974-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fc974-126">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="fc974-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fc974-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fc974-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fc974-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fc974-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
