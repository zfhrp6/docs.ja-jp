---
title: 214 - OperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6ef1eb398a0146e619cbcb85fe2761306aba4fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="034a6-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="034a6-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="034a6-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="034a6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="034a6-104">ID</span><span class="sxs-lookup"><span data-stu-id="034a6-104">ID</span></span>|<span data-ttu-id="034a6-105">214</span><span class="sxs-lookup"><span data-stu-id="034a6-105">214</span></span>|  
|<span data-ttu-id="034a6-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="034a6-106">Keywords</span></span>|<span data-ttu-id="034a6-107">HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="034a6-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="034a6-108">レベル</span><span class="sxs-lookup"><span data-stu-id="034a6-108">Level</span></span>|<span data-ttu-id="034a6-109">情報</span><span class="sxs-lookup"><span data-stu-id="034a6-109">Information</span></span>|  
|<span data-ttu-id="034a6-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="034a6-110">Channel</span></span>|<span data-ttu-id="034a6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="034a6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="034a6-112">説明</span><span class="sxs-lookup"><span data-stu-id="034a6-112">Description</span></span>  
 <span data-ttu-id="034a6-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、メソッドから例外がスローされることなく、メソッドへの呼び出しを完了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="034a6-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="034a6-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="034a6-114">Message</span></span>  
 <span data-ttu-id="034a6-115">OperationInvoker がメソッド '%1' への呼び出しを完了しました。</span><span class="sxs-lookup"><span data-stu-id="034a6-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="034a6-116">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="034a6-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="034a6-117">詳細</span><span class="sxs-lookup"><span data-stu-id="034a6-117">Details</span></span>  
  
|<span data-ttu-id="034a6-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="034a6-118">Data Item Name</span></span>|<span data-ttu-id="034a6-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="034a6-119">Data Item Type</span></span>|<span data-ttu-id="034a6-120">説明</span><span class="sxs-lookup"><span data-stu-id="034a6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="034a6-121">メソッド名</span><span class="sxs-lookup"><span data-stu-id="034a6-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="034a6-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="034a6-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="034a6-123">存続期間</span><span class="sxs-lookup"><span data-stu-id="034a6-123">Duration</span></span>|`xs:long`|<span data-ttu-id="034a6-124">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="034a6-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="034a6-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="034a6-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="034a6-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="034a6-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="034a6-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス & #124 です。サービス仮想パス & #124 です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="034a6-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="034a6-128">例: ' 既定の Web サイト/CalculatorApplication & #124;/CalculatorService.svc & #124 です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="034a6-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="034a6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="034a6-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="034a6-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="034a6-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
