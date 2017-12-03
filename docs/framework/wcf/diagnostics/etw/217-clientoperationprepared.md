---
title: 217 - ClientOperationPrepared
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea5526c39d8947a578174dd4d58685249b4952e1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="485ac-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="485ac-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="485ac-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="485ac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="485ac-104">ID</span><span class="sxs-lookup"><span data-stu-id="485ac-104">ID</span></span>|<span data-ttu-id="485ac-105">217</span><span class="sxs-lookup"><span data-stu-id="485ac-105">217</span></span>|  
|<span data-ttu-id="485ac-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="485ac-106">Keywords</span></span>|<span data-ttu-id="485ac-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="485ac-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="485ac-108">レベル</span><span class="sxs-lookup"><span data-stu-id="485ac-108">Level</span></span>|<span data-ttu-id="485ac-109">情報</span><span class="sxs-lookup"><span data-stu-id="485ac-109">Information</span></span>|  
|<span data-ttu-id="485ac-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="485ac-110">Channel</span></span>|<span data-ttu-id="485ac-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="485ac-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="485ac-112">説明</span><span class="sxs-lookup"><span data-stu-id="485ac-112">Description</span></span>  
 <span data-ttu-id="485ac-113">このイベントは、操作がサービスに送信される直前に、クライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="485ac-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="485ac-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="485ac-114">Message</span></span>  
 <span data-ttu-id="485ac-115">クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。</span><span class="sxs-lookup"><span data-stu-id="485ac-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="485ac-116">メッセージは '%3' に送信されます。</span><span class="sxs-lookup"><span data-stu-id="485ac-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="485ac-117">詳細</span><span class="sxs-lookup"><span data-stu-id="485ac-117">Details</span></span>  
  
|<span data-ttu-id="485ac-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="485ac-118">Data Item Name</span></span>|<span data-ttu-id="485ac-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="485ac-119">Data Item Type</span></span>|<span data-ttu-id="485ac-120">説明</span><span class="sxs-lookup"><span data-stu-id="485ac-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="485ac-121">操作</span><span class="sxs-lookup"><span data-stu-id="485ac-121">Action</span></span>|`xs:string`|<span data-ttu-id="485ac-122">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="485ac-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="485ac-123">Contract Name</span><span class="sxs-lookup"><span data-stu-id="485ac-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="485ac-124">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="485ac-124">The name of the contract.</span></span> <span data-ttu-id="485ac-125">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="485ac-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="485ac-126">保存先</span><span class="sxs-lookup"><span data-stu-id="485ac-126">Destination</span></span>|`xs:string`|<span data-ttu-id="485ac-127">メッセージの送信先となるサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="485ac-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="485ac-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="485ac-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="485ac-129">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="485ac-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="485ac-130">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="485ac-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="485ac-131">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="485ac-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="485ac-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="485ac-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="485ac-133">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="485ac-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
