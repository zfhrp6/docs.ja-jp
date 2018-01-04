---
title: 215 - MessageReceivedByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bf2336d1b5c9dda1dac2b38305d944a822bd253
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="1aeea-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="1aeea-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="1aeea-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aeea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1aeea-104">ID</span><span class="sxs-lookup"><span data-stu-id="1aeea-104">ID</span></span>|<span data-ttu-id="1aeea-105">215</span><span class="sxs-lookup"><span data-stu-id="1aeea-105">215</span></span>|  
|<span data-ttu-id="1aeea-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1aeea-106">Keywords</span></span>|<span data-ttu-id="1aeea-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1aeea-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1aeea-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1aeea-108">Level</span></span>|<span data-ttu-id="1aeea-109">情報</span><span class="sxs-lookup"><span data-stu-id="1aeea-109">Information</span></span>|  
|<span data-ttu-id="1aeea-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1aeea-110">Channel</span></span>|<span data-ttu-id="1aeea-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1aeea-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1aeea-112">説明</span><span class="sxs-lookup"><span data-stu-id="1aeea-112">Description</span></span>  
 <span data-ttu-id="1aeea-113">このイベントは、TCP ベースのトランスポートがメッセージを受信するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="1aeea-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="1aeea-114">トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1aeea-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="1aeea-115">これはインフラストラクチャの動作によるもので、セキュリティがその一例です。</span><span class="sxs-lookup"><span data-stu-id="1aeea-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="1aeea-116">そのため、生成される `MessageReceivedByTransport` イベントの数が、サービスのバインディングとその構成に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="1aeea-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1aeea-117">一方向トランスポートでは、このイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="1aeea-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1aeea-118">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1aeea-118">Message</span></span>  
 <span data-ttu-id="1aeea-119">トランスポートが '%1' からメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="1aeea-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1aeea-120">詳細</span><span class="sxs-lookup"><span data-stu-id="1aeea-120">Details</span></span>  
  
|<span data-ttu-id="1aeea-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1aeea-121">Data Item Name</span></span>|<span data-ttu-id="1aeea-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1aeea-122">Data Item Type</span></span>|<span data-ttu-id="1aeea-123">説明</span><span class="sxs-lookup"><span data-stu-id="1aeea-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1aeea-124">Listen Address</span><span class="sxs-lookup"><span data-stu-id="1aeea-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="1aeea-125">メッセージを受信したアドレス。</span><span class="sxs-lookup"><span data-stu-id="1aeea-125">The address that received the message.</span></span>|  
|<span data-ttu-id="1aeea-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="1aeea-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="1aeea-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="1aeea-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1aeea-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="1aeea-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1aeea-129">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="1aeea-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1aeea-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1aeea-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1aeea-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1aeea-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
