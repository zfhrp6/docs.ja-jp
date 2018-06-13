---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459420"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="db145-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="db145-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="db145-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="db145-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db145-104">ID</span><span class="sxs-lookup"><span data-stu-id="db145-104">ID</span></span>|<span data-ttu-id="db145-105">223</span><span class="sxs-lookup"><span data-stu-id="db145-105">223</span></span>|  
|<span data-ttu-id="db145-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="db145-106">Keywords</span></span>|<span data-ttu-id="db145-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="db145-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="db145-108">レベル</span><span class="sxs-lookup"><span data-stu-id="db145-108">Level</span></span>|<span data-ttu-id="db145-109">警告</span><span class="sxs-lookup"><span data-stu-id="db145-109">Warning</span></span>|  
|<span data-ttu-id="db145-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="db145-110">Channel</span></span>|<span data-ttu-id="db145-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="db145-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db145-112">説明</span><span class="sxs-lookup"><span data-stu-id="db145-112">Description</span></span>  
 <span data-ttu-id="db145-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に `FaultException` から派生する例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="db145-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db145-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="db145-114">Message</span></span>  
 <span data-ttu-id="db145-115">OperationInvoker によって呼び出されたメソッド '%1' で FaultException がスローされました。</span><span class="sxs-lookup"><span data-stu-id="db145-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="db145-116">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="db145-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db145-117">説明</span><span class="sxs-lookup"><span data-stu-id="db145-117">Details</span></span>  
  
|<span data-ttu-id="db145-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="db145-118">Data Item Name</span></span>|<span data-ttu-id="db145-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="db145-119">Data Item Type</span></span>|<span data-ttu-id="db145-120">説明</span><span class="sxs-lookup"><span data-stu-id="db145-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db145-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="db145-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="db145-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="db145-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="db145-123">存続期間</span><span class="sxs-lookup"><span data-stu-id="db145-123">Duration</span></span>|`xs:long`|<span data-ttu-id="db145-124">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="db145-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="db145-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="db145-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="db145-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="db145-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="db145-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="db145-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="db145-128">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="db145-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="db145-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db145-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="db145-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="db145-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
