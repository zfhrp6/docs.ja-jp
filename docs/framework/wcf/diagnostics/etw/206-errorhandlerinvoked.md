---
title: 206 - ErrorHandlerInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43acd7ae7bbfc84e1d1ffb1bf4fa49a3dd3f191a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="34485-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="34485-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="34485-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34485-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34485-104">ID</span><span class="sxs-lookup"><span data-stu-id="34485-104">ID</span></span>|<span data-ttu-id="34485-105">206</span><span class="sxs-lookup"><span data-stu-id="34485-105">206</span></span>|  
|<span data-ttu-id="34485-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="34485-106">Keywords</span></span>|<span data-ttu-id="34485-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="34485-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="34485-108">レベル</span><span class="sxs-lookup"><span data-stu-id="34485-108">Level</span></span>|<span data-ttu-id="34485-109">情報</span><span class="sxs-lookup"><span data-stu-id="34485-109">Information</span></span>|  
|<span data-ttu-id="34485-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="34485-110">Channel</span></span>|<span data-ttu-id="34485-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="34485-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="34485-112">説明</span><span class="sxs-lookup"><span data-stu-id="34485-112">Description</span></span>  
 <span data-ttu-id="34485-113">このイベントは、サービス操作中に発生した例外を処理する機会が `ErrorHandler` に与えられた後に、生成されます。</span><span class="sxs-lookup"><span data-stu-id="34485-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="34485-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="34485-114">Message</span></span>  
 <span data-ttu-id="34485-115">ディスパッチャーは、型 '%3' の例外がスロー型 '%1' の ErrorHandler を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="34485-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="34485-116">ErrorHandled == '%2'。</span><span class="sxs-lookup"><span data-stu-id="34485-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="34485-117">説明</span><span class="sxs-lookup"><span data-stu-id="34485-117">Details</span></span>  
  
|<span data-ttu-id="34485-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="34485-118">Data Item Name</span></span>|<span data-ttu-id="34485-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="34485-119">Data Item Type</span></span>|<span data-ttu-id="34485-120">説明</span><span class="sxs-lookup"><span data-stu-id="34485-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="34485-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="34485-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="34485-122">呼び出された `ErrorHandler` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="34485-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="34485-123">Handled</span><span class="sxs-lookup"><span data-stu-id="34485-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="34485-124">エラー ハンドラーがエラーを処理した場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="34485-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="34485-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="34485-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="34485-126">処理対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="34485-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="34485-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="34485-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="34485-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="34485-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="34485-129">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="34485-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="34485-130">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="34485-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="34485-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="34485-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="34485-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="34485-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
