---
title: 220 - MessageSentToTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7bc3b784dca090ed768711728a054782e06c7b10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="24133-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="24133-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="24133-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="24133-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24133-104">ID</span><span class="sxs-lookup"><span data-stu-id="24133-104">Id</span></span>|<span data-ttu-id="24133-105">220</span><span class="sxs-lookup"><span data-stu-id="24133-105">220</span></span>|  
|<span data-ttu-id="24133-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="24133-106">Keywords</span></span>|<span data-ttu-id="24133-107">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24133-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="24133-108">レベル</span><span class="sxs-lookup"><span data-stu-id="24133-108">Level</span></span>|<span data-ttu-id="24133-109">情報</span><span class="sxs-lookup"><span data-stu-id="24133-109">Information</span></span>|  
|<span data-ttu-id="24133-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="24133-110">Channel</span></span>|<span data-ttu-id="24133-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="24133-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24133-112">説明</span><span class="sxs-lookup"><span data-stu-id="24133-112">Description</span></span>  
 <span data-ttu-id="24133-113">このイベントは、サービス モデルがトランスポートにメッセージを送信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="24133-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24133-114">一方向トランスポートでは、このイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="24133-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24133-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="24133-115">Message</span></span>  
 <span data-ttu-id="24133-116">ディスパッチャーがトランスポートにメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="24133-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="24133-117">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="24133-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="24133-118">詳細</span><span class="sxs-lookup"><span data-stu-id="24133-118">Details</span></span>  
  
|<span data-ttu-id="24133-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="24133-119">Data Item Name</span></span>|<span data-ttu-id="24133-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="24133-120">Data Item Type</span></span>|<span data-ttu-id="24133-121">説明</span><span class="sxs-lookup"><span data-stu-id="24133-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24133-122">Correlation ID</span><span class="sxs-lookup"><span data-stu-id="24133-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="24133-123">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="24133-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="24133-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="24133-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="24133-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="24133-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="24133-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="24133-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="24133-127">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="24133-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="24133-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="24133-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="24133-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="24133-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
