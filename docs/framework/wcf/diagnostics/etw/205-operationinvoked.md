---
title: 205 - OperationInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b0a96f1e3ba72a226d9b1a871382a27db61c57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="19f6c-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="19f6c-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="19f6c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="19f6c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19f6c-104">ID</span><span class="sxs-lookup"><span data-stu-id="19f6c-104">ID</span></span>|<span data-ttu-id="19f6c-105">205</span><span class="sxs-lookup"><span data-stu-id="19f6c-105">205</span></span>|  
|<span data-ttu-id="19f6c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="19f6c-106">Keywords</span></span>|<span data-ttu-id="19f6c-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="19f6c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="19f6c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="19f6c-108">Level</span></span>|<span data-ttu-id="19f6c-109">情報</span><span class="sxs-lookup"><span data-stu-id="19f6c-109">Information</span></span>|  
|<span data-ttu-id="19f6c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="19f6c-110">Channel</span></span>|<span data-ttu-id="19f6c-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="19f6c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="19f6c-112">説明</span><span class="sxs-lookup"><span data-stu-id="19f6c-112">Description</span></span>  
 <span data-ttu-id="19f6c-113">このイベントは、サービス モデルの既定の `OperationInvoker` がメソッドの呼び出しを開始する直前に生成されます。</span><span class="sxs-lookup"><span data-stu-id="19f6c-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="19f6c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="19f6c-114">Message</span></span>  
 <span data-ttu-id="19f6c-115">OperationInvoker が '%1' メソッドを呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="19f6c-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="19f6c-116">呼び出し元の情報: '%2'。</span><span class="sxs-lookup"><span data-stu-id="19f6c-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="19f6c-117">詳細</span><span class="sxs-lookup"><span data-stu-id="19f6c-117">Details</span></span>  
  
|<span data-ttu-id="19f6c-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="19f6c-118">Data Item Name</span></span>|<span data-ttu-id="19f6c-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="19f6c-119">Data Item Type</span></span>|<span data-ttu-id="19f6c-120">説明</span><span class="sxs-lookup"><span data-stu-id="19f6c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="19f6c-121">メソッド名</span><span class="sxs-lookup"><span data-stu-id="19f6c-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="19f6c-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="19f6c-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="19f6c-123">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="19f6c-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="19f6c-124">クライアントの IP アドレスとポート番号。'<IP アドレス>:<ポート番号>' の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="19f6c-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="19f6c-125">この 2 つの値は、操作コンテキスト内の 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' メッセージ プロパティから取得します。</span><span class="sxs-lookup"><span data-stu-id="19f6c-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="19f6c-126">TCP 以外のバインドの場合、この値は `null` になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="19f6c-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="19f6c-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="19f6c-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="19f6c-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="19f6c-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="19f6c-129">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="19f6c-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="19f6c-130">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="19f6c-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="19f6c-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="19f6c-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="19f6c-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="19f6c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
