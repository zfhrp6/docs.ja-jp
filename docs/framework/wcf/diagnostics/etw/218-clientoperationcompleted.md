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
ms.workload: dotnet
ms.openlocfilehash: 974fde79d8b24c17928fa4ff38bb9d35d6b5a815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="02768-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="02768-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="02768-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="02768-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02768-104">ID</span><span class="sxs-lookup"><span data-stu-id="02768-104">ID</span></span>|<span data-ttu-id="02768-105">218</span><span class="sxs-lookup"><span data-stu-id="02768-105">218</span></span>|  
|<span data-ttu-id="02768-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="02768-106">Keywords</span></span>|<span data-ttu-id="02768-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="02768-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="02768-108">レベル</span><span class="sxs-lookup"><span data-stu-id="02768-108">Level</span></span>|<span data-ttu-id="02768-109">情報</span><span class="sxs-lookup"><span data-stu-id="02768-109">Information</span></span>|  
|<span data-ttu-id="02768-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="02768-110">Channel</span></span>|<span data-ttu-id="02768-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="02768-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="02768-112">説明</span><span class="sxs-lookup"><span data-stu-id="02768-112">Description</span></span>  
 <span data-ttu-id="02768-113">このイベントは、ある操作が完了した直後にクライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="02768-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="02768-114">一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="02768-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="02768-115">要求 - 応答の操作の場合は、応答の受信後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="02768-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="02768-116">メッセージ</span><span class="sxs-lookup"><span data-stu-id="02768-116">Message</span></span>  
 <span data-ttu-id="02768-117">クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。</span><span class="sxs-lookup"><span data-stu-id="02768-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="02768-118">メッセージは '%3' に送信されました。</span><span class="sxs-lookup"><span data-stu-id="02768-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="02768-119">説明</span><span class="sxs-lookup"><span data-stu-id="02768-119">Details</span></span>  
  
|<span data-ttu-id="02768-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="02768-120">Data Item Name</span></span>|<span data-ttu-id="02768-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="02768-121">Data Item Type</span></span>|<span data-ttu-id="02768-122">説明</span><span class="sxs-lookup"><span data-stu-id="02768-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="02768-123">アクション</span><span class="sxs-lookup"><span data-stu-id="02768-123">Action</span></span>|<span data-ttu-id="02768-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="02768-124">xs:string</span></span>|<span data-ttu-id="02768-125">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="02768-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="02768-126">Contract Name</span><span class="sxs-lookup"><span data-stu-id="02768-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="02768-127">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="02768-127">The name of the contract.</span></span> <span data-ttu-id="02768-128">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="02768-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="02768-129">保存先</span><span class="sxs-lookup"><span data-stu-id="02768-129">Destination</span></span>|`xs:string`|<span data-ttu-id="02768-130">メッセージの送信先のサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="02768-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="02768-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="02768-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="02768-132">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="02768-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="02768-133">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="02768-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="02768-134">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="02768-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="02768-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="02768-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="02768-136">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="02768-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
