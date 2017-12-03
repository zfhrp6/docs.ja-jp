---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0428d90135823761e7b8a12f560786e34e12734
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="ff1af-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="ff1af-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="ff1af-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ff1af-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff1af-104">ID</span><span class="sxs-lookup"><span data-stu-id="ff1af-104">ID</span></span>|<span data-ttu-id="ff1af-105">223</span><span class="sxs-lookup"><span data-stu-id="ff1af-105">223</span></span>|  
|<span data-ttu-id="ff1af-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ff1af-106">Keywords</span></span>|<span data-ttu-id="ff1af-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ff1af-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ff1af-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ff1af-108">Level</span></span>|<span data-ttu-id="ff1af-109">警告</span><span class="sxs-lookup"><span data-stu-id="ff1af-109">Warning</span></span>|  
|<span data-ttu-id="ff1af-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ff1af-110">Channel</span></span>|<span data-ttu-id="ff1af-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ff1af-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff1af-112">説明</span><span class="sxs-lookup"><span data-stu-id="ff1af-112">Description</span></span>  
 <span data-ttu-id="ff1af-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に `FaultException` から派生する例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="ff1af-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff1af-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ff1af-114">Message</span></span>  
 <span data-ttu-id="ff1af-115">OperationInvoker によって呼び出されたメソッド '%1' で FaultException がスローされました。</span><span class="sxs-lookup"><span data-stu-id="ff1af-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="ff1af-116">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="ff1af-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff1af-117">詳細</span><span class="sxs-lookup"><span data-stu-id="ff1af-117">Details</span></span>  
  
|<span data-ttu-id="ff1af-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ff1af-118">Data Item Name</span></span>|<span data-ttu-id="ff1af-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ff1af-119">Data Item Type</span></span>|<span data-ttu-id="ff1af-120">説明</span><span class="sxs-lookup"><span data-stu-id="ff1af-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff1af-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="ff1af-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="ff1af-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="ff1af-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="ff1af-123">存続期間</span><span class="sxs-lookup"><span data-stu-id="ff1af-123">Duration</span></span>|`xs:long`|<span data-ttu-id="ff1af-124">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="ff1af-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="ff1af-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="ff1af-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="ff1af-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="ff1af-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ff1af-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="ff1af-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ff1af-128">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="ff1af-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ff1af-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ff1af-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ff1af-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ff1af-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
