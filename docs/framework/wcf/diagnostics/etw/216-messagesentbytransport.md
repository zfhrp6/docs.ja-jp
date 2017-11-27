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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b35f46ae7a214ab45e4062928de82c4da6541a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="dfda7-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="dfda7-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="dfda7-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dfda7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dfda7-104">ID</span><span class="sxs-lookup"><span data-stu-id="dfda7-104">ID</span></span>|<span data-ttu-id="dfda7-105">216</span><span class="sxs-lookup"><span data-stu-id="dfda7-105">216</span></span>|  
|<span data-ttu-id="dfda7-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="dfda7-106">Keywords</span></span>|<span data-ttu-id="dfda7-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dfda7-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="dfda7-108">レベル</span><span class="sxs-lookup"><span data-stu-id="dfda7-108">Level</span></span>|<span data-ttu-id="dfda7-109">情報</span><span class="sxs-lookup"><span data-stu-id="dfda7-109">Information</span></span>|  
|<span data-ttu-id="dfda7-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="dfda7-110">Channel</span></span>|<span data-ttu-id="dfda7-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="dfda7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dfda7-112">説明</span><span class="sxs-lookup"><span data-stu-id="dfda7-112">Description</span></span>  
 <span data-ttu-id="dfda7-113">このイベントは、TCP ベースのトランスポートがメッセージを送信するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="dfda7-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="dfda7-114">トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="dfda7-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="dfda7-115">これはインフラストラクチャの動作によるもので、セキュリティがその一例です。</span><span class="sxs-lookup"><span data-stu-id="dfda7-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="dfda7-116">そのため、数**MessageSentByTransport**が生成されるイベント、サービスのバインディングとその構成に基づき、異なります。</span><span class="sxs-lookup"><span data-stu-id="dfda7-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dfda7-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="dfda7-117">Message</span></span>  
 <span data-ttu-id="dfda7-118">トランスポートが '%1' にメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="dfda7-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dfda7-119">詳細</span><span class="sxs-lookup"><span data-stu-id="dfda7-119">Details</span></span>  
  
|<span data-ttu-id="dfda7-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="dfda7-120">Data Item Name</span></span>|<span data-ttu-id="dfda7-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="dfda7-121">Data Item Type</span></span>|<span data-ttu-id="dfda7-122">説明</span><span class="sxs-lookup"><span data-stu-id="dfda7-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dfda7-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="dfda7-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="dfda7-124">要求メッセージが送信されたアドレス。</span><span class="sxs-lookup"><span data-stu-id="dfda7-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="dfda7-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="dfda7-125">HostReference</span></span>|<span data-ttu-id="dfda7-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="dfda7-126">xs:string</span></span>|<span data-ttu-id="dfda7-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="dfda7-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dfda7-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="dfda7-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dfda7-129">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="dfda7-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dfda7-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dfda7-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dfda7-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="dfda7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
