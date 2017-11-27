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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84470cbaf7ba7951ef59b130c696462079216cde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="1f2e9-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="1f2e9-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1f2e9-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1f2e9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1f2e9-104">ID</span><span class="sxs-lookup"><span data-stu-id="1f2e9-104">ID</span></span>|<span data-ttu-id="1f2e9-105">206</span><span class="sxs-lookup"><span data-stu-id="1f2e9-105">206</span></span>|  
|<span data-ttu-id="1f2e9-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1f2e9-106">Keywords</span></span>|<span data-ttu-id="1f2e9-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f2e9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1f2e9-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1f2e9-108">Level</span></span>|<span data-ttu-id="1f2e9-109">情報</span><span class="sxs-lookup"><span data-stu-id="1f2e9-109">Information</span></span>|  
|<span data-ttu-id="1f2e9-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1f2e9-110">Channel</span></span>|<span data-ttu-id="1f2e9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1f2e9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1f2e9-112">説明</span><span class="sxs-lookup"><span data-stu-id="1f2e9-112">Description</span></span>  
 <span data-ttu-id="1f2e9-113">このイベントは、サービス操作中に発生した例外を処理する機会が `ErrorHandler` に与えられた後に、生成されます。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1f2e9-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1f2e9-114">Message</span></span>  
 <span data-ttu-id="1f2e9-115">ディスパッチャーは、型 '%3' の例外がスロー型 '%1' の ErrorHandler を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="1f2e9-116">ErrorHandled == '%2'。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1f2e9-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1f2e9-117">Details</span></span>  
  
|<span data-ttu-id="1f2e9-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1f2e9-118">Data Item Name</span></span>|<span data-ttu-id="1f2e9-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1f2e9-119">Data Item Type</span></span>|<span data-ttu-id="1f2e9-120">説明</span><span class="sxs-lookup"><span data-stu-id="1f2e9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1f2e9-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="1f2e9-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="1f2e9-122">呼び出された `ErrorHandler` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="1f2e9-123">Handled</span><span class="sxs-lookup"><span data-stu-id="1f2e9-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="1f2e9-124">エラー ハンドラーがエラーを処理した場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="1f2e9-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="1f2e9-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="1f2e9-126">処理対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="1f2e9-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="1f2e9-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="1f2e9-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1f2e9-129">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1f2e9-130">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1f2e9-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1f2e9-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1f2e9-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1f2e9-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
