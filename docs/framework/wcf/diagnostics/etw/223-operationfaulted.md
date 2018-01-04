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
ms.workload: dotnet
ms.openlocfilehash: fcaea7b98bc57bcac901ac659786175a10799700
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="2eebf-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="2eebf-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="2eebf-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2eebf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2eebf-104">ID</span><span class="sxs-lookup"><span data-stu-id="2eebf-104">ID</span></span>|<span data-ttu-id="2eebf-105">223</span><span class="sxs-lookup"><span data-stu-id="2eebf-105">223</span></span>|  
|<span data-ttu-id="2eebf-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2eebf-106">Keywords</span></span>|<span data-ttu-id="2eebf-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2eebf-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2eebf-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2eebf-108">Level</span></span>|<span data-ttu-id="2eebf-109">警告</span><span class="sxs-lookup"><span data-stu-id="2eebf-109">Warning</span></span>|  
|<span data-ttu-id="2eebf-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2eebf-110">Channel</span></span>|<span data-ttu-id="2eebf-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2eebf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2eebf-112">説明</span><span class="sxs-lookup"><span data-stu-id="2eebf-112">Description</span></span>  
 <span data-ttu-id="2eebf-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に `FaultException` から派生する例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="2eebf-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2eebf-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2eebf-114">Message</span></span>  
 <span data-ttu-id="2eebf-115">OperationInvoker によって呼び出されたメソッド '%1' で FaultException がスローされました。</span><span class="sxs-lookup"><span data-stu-id="2eebf-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="2eebf-116">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="2eebf-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2eebf-117">説明</span><span class="sxs-lookup"><span data-stu-id="2eebf-117">Details</span></span>  
  
|<span data-ttu-id="2eebf-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2eebf-118">Data Item Name</span></span>|<span data-ttu-id="2eebf-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2eebf-119">Data Item Type</span></span>|<span data-ttu-id="2eebf-120">説明</span><span class="sxs-lookup"><span data-stu-id="2eebf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2eebf-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="2eebf-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="2eebf-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="2eebf-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="2eebf-123">存続期間</span><span class="sxs-lookup"><span data-stu-id="2eebf-123">Duration</span></span>|`xs:long`|<span data-ttu-id="2eebf-124">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="2eebf-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="2eebf-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="2eebf-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="2eebf-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="2eebf-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2eebf-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="2eebf-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2eebf-128">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="2eebf-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2eebf-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2eebf-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2eebf-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2eebf-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
