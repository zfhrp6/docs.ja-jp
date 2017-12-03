---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b2bf2841c04dcdc74bf64a0169b95caa6c8a36a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="fce97-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="fce97-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="fce97-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fce97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fce97-104">ID</span><span class="sxs-lookup"><span data-stu-id="fce97-104">ID</span></span>|<span data-ttu-id="fce97-105">216</span><span class="sxs-lookup"><span data-stu-id="fce97-105">216</span></span>|  
|<span data-ttu-id="fce97-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fce97-106">Keywords</span></span>|<span data-ttu-id="fce97-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fce97-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fce97-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fce97-108">Level</span></span>|<span data-ttu-id="fce97-109">情報</span><span class="sxs-lookup"><span data-stu-id="fce97-109">Information</span></span>|  
|<span data-ttu-id="fce97-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fce97-110">Channel</span></span>|<span data-ttu-id="fce97-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fce97-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fce97-112">説明</span><span class="sxs-lookup"><span data-stu-id="fce97-112">Description</span></span>  
 <span data-ttu-id="fce97-113">このイベントは、TCP ベースのトランスポートがメッセージを送信するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fce97-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="fce97-114">トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="fce97-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="fce97-115">これはインフラストラクチャの動作によるもので、セキュリティがその一例です。</span><span class="sxs-lookup"><span data-stu-id="fce97-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="fce97-116">そのため、数**MessageSentByTransport**が生成されるイベント、サービスのバインディングとその構成に基づき、異なります。</span><span class="sxs-lookup"><span data-stu-id="fce97-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fce97-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fce97-117">Message</span></span>  
 <span data-ttu-id="fce97-118">トランスポートが '%1' にメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="fce97-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fce97-119">詳細</span><span class="sxs-lookup"><span data-stu-id="fce97-119">Details</span></span>  
  
|<span data-ttu-id="fce97-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fce97-120">Data Item Name</span></span>|<span data-ttu-id="fce97-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fce97-121">Data Item Type</span></span>|<span data-ttu-id="fce97-122">説明</span><span class="sxs-lookup"><span data-stu-id="fce97-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fce97-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="fce97-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="fce97-124">要求メッセージが送信されたアドレス。</span><span class="sxs-lookup"><span data-stu-id="fce97-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="fce97-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="fce97-125">HostReference</span></span>|<span data-ttu-id="fce97-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="fce97-126">xs:string</span></span>|<span data-ttu-id="fce97-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="fce97-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fce97-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="fce97-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fce97-129">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="fce97-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fce97-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fce97-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fce97-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fce97-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
