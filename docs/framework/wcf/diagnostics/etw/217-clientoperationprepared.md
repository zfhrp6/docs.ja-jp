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
ms.workload: dotnet
ms.openlocfilehash: 3e1b4e3aab6a6a7f94bfb3783c9e32f83557db19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="7c324-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="7c324-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="7c324-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7c324-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c324-104">ID</span><span class="sxs-lookup"><span data-stu-id="7c324-104">ID</span></span>|<span data-ttu-id="7c324-105">217</span><span class="sxs-lookup"><span data-stu-id="7c324-105">217</span></span>|  
|<span data-ttu-id="7c324-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7c324-106">Keywords</span></span>|<span data-ttu-id="7c324-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7c324-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7c324-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7c324-108">Level</span></span>|<span data-ttu-id="7c324-109">情報</span><span class="sxs-lookup"><span data-stu-id="7c324-109">Information</span></span>|  
|<span data-ttu-id="7c324-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7c324-110">Channel</span></span>|<span data-ttu-id="7c324-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7c324-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7c324-112">説明</span><span class="sxs-lookup"><span data-stu-id="7c324-112">Description</span></span>  
 <span data-ttu-id="7c324-113">このイベントは、操作がサービスに送信される直前に、クライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c324-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7c324-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7c324-114">Message</span></span>  
 <span data-ttu-id="7c324-115">クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。</span><span class="sxs-lookup"><span data-stu-id="7c324-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="7c324-116">メッセージは '%3' に送信されます。</span><span class="sxs-lookup"><span data-stu-id="7c324-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7c324-117">説明</span><span class="sxs-lookup"><span data-stu-id="7c324-117">Details</span></span>  
  
|<span data-ttu-id="7c324-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7c324-118">Data Item Name</span></span>|<span data-ttu-id="7c324-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7c324-119">Data Item Type</span></span>|<span data-ttu-id="7c324-120">説明</span><span class="sxs-lookup"><span data-stu-id="7c324-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7c324-121">アクション</span><span class="sxs-lookup"><span data-stu-id="7c324-121">Action</span></span>|`xs:string`|<span data-ttu-id="7c324-122">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="7c324-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="7c324-123">Contract Name</span><span class="sxs-lookup"><span data-stu-id="7c324-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="7c324-124">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="7c324-124">The name of the contract.</span></span> <span data-ttu-id="7c324-125">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="7c324-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="7c324-126">保存先</span><span class="sxs-lookup"><span data-stu-id="7c324-126">Destination</span></span>|`xs:string`|<span data-ttu-id="7c324-127">メッセージの送信先となるサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="7c324-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="7c324-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="7c324-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="7c324-129">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="7c324-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7c324-130">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="7c324-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7c324-131">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="7c324-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7c324-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7c324-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7c324-133">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7c324-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
