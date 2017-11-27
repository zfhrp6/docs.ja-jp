---
title: 222 - OperationFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c76b502c9c1a767898b1e857c2e943c26fad5c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="fe472-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="fe472-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="fe472-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fe472-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe472-104">ID</span><span class="sxs-lookup"><span data-stu-id="fe472-104">ID</span></span>|<span data-ttu-id="fe472-105">222</span><span class="sxs-lookup"><span data-stu-id="fe472-105">222</span></span>|  
|<span data-ttu-id="fe472-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fe472-106">Keywords</span></span>|<span data-ttu-id="fe472-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe472-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fe472-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fe472-108">Level</span></span>|<span data-ttu-id="fe472-109">警告</span><span class="sxs-lookup"><span data-stu-id="fe472-109">Warning</span></span>|  
|<span data-ttu-id="fe472-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fe472-110">Channel</span></span>|<span data-ttu-id="fe472-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fe472-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fe472-112">説明</span><span class="sxs-lookup"><span data-stu-id="fe472-112">Description</span></span>  
 <span data-ttu-id="fe472-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="fe472-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="fe472-114">`FaultException` から派生する例外では、このイベントは生成されません。</span><span class="sxs-lookup"><span data-stu-id="fe472-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fe472-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fe472-115">Message</span></span>  
 <span data-ttu-id="fe472-116">OperationInvoker によって呼び出されたメソッド '%1' で、ハンドルされない例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="fe472-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="fe472-117">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="fe472-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fe472-118">詳細</span><span class="sxs-lookup"><span data-stu-id="fe472-118">Details</span></span>  
  
|<span data-ttu-id="fe472-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fe472-119">Data Item Name</span></span>|<span data-ttu-id="fe472-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fe472-120">Data Item Type</span></span>|<span data-ttu-id="fe472-121">説明</span><span class="sxs-lookup"><span data-stu-id="fe472-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fe472-122">メソッド名</span><span class="sxs-lookup"><span data-stu-id="fe472-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="fe472-123">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="fe472-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="fe472-124">存続期間</span><span class="sxs-lookup"><span data-stu-id="fe472-124">Duration</span></span>|`xs:long`|<span data-ttu-id="fe472-125">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="fe472-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="fe472-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="fe472-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="fe472-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="fe472-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fe472-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="fe472-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fe472-129">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="fe472-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fe472-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fe472-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fe472-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fe472-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
