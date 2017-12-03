---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d5b6fcc1c7ec4dd2f2c008e9d8bcfb58b2b4991
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="e56f9-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="e56f9-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="e56f9-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e56f9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e56f9-104">ID</span><span class="sxs-lookup"><span data-stu-id="e56f9-104">ID</span></span>|<span data-ttu-id="e56f9-105">218</span><span class="sxs-lookup"><span data-stu-id="e56f9-105">218</span></span>|  
|<span data-ttu-id="e56f9-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e56f9-106">Keywords</span></span>|<span data-ttu-id="e56f9-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e56f9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e56f9-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e56f9-108">Level</span></span>|<span data-ttu-id="e56f9-109">情報</span><span class="sxs-lookup"><span data-stu-id="e56f9-109">Information</span></span>|  
|<span data-ttu-id="e56f9-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e56f9-110">Channel</span></span>|<span data-ttu-id="e56f9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e56f9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e56f9-112">説明</span><span class="sxs-lookup"><span data-stu-id="e56f9-112">Description</span></span>  
 <span data-ttu-id="e56f9-113">このイベントは、ある操作が完了した直後にクライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="e56f9-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="e56f9-114">一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e56f9-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="e56f9-115">要求 - 応答の操作の場合は、応答の受信後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e56f9-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e56f9-116">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e56f9-116">Message</span></span>  
 <span data-ttu-id="e56f9-117">クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。</span><span class="sxs-lookup"><span data-stu-id="e56f9-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="e56f9-118">メッセージは '%3' に送信されました。</span><span class="sxs-lookup"><span data-stu-id="e56f9-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e56f9-119">詳細</span><span class="sxs-lookup"><span data-stu-id="e56f9-119">Details</span></span>  
  
|<span data-ttu-id="e56f9-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e56f9-120">Data Item Name</span></span>|<span data-ttu-id="e56f9-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e56f9-121">Data Item Type</span></span>|<span data-ttu-id="e56f9-122">説明</span><span class="sxs-lookup"><span data-stu-id="e56f9-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e56f9-123">アクション</span><span class="sxs-lookup"><span data-stu-id="e56f9-123">Action</span></span>|<span data-ttu-id="e56f9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e56f9-124">xs:string</span></span>|<span data-ttu-id="e56f9-125">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="e56f9-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="e56f9-126">Contract Name</span><span class="sxs-lookup"><span data-stu-id="e56f9-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="e56f9-127">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="e56f9-127">The name of the contract.</span></span> <span data-ttu-id="e56f9-128">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="e56f9-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="e56f9-129">保存先</span><span class="sxs-lookup"><span data-stu-id="e56f9-129">Destination</span></span>|`xs:string`|<span data-ttu-id="e56f9-130">メッセージの送信先のサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="e56f9-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="e56f9-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="e56f9-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="e56f9-132">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="e56f9-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e56f9-133">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="e56f9-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e56f9-134">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="e56f9-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e56f9-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e56f9-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e56f9-136">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e56f9-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
