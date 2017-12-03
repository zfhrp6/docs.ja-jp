---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fce60ca658c159df11588be149cda17ad2303d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="7cdae-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="7cdae-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="7cdae-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7cdae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7cdae-104">ID</span><span class="sxs-lookup"><span data-stu-id="7cdae-104">ID</span></span>|<span data-ttu-id="7cdae-105">207</span><span class="sxs-lookup"><span data-stu-id="7cdae-105">207</span></span>|  
|<span data-ttu-id="7cdae-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7cdae-106">Keywords</span></span>|<span data-ttu-id="7cdae-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7cdae-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7cdae-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7cdae-108">Level</span></span>|<span data-ttu-id="7cdae-109">情報</span><span class="sxs-lookup"><span data-stu-id="7cdae-109">Information</span></span>|  
|<span data-ttu-id="7cdae-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7cdae-110">Channel</span></span>|<span data-ttu-id="7cdae-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7cdae-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7cdae-112">説明</span><span class="sxs-lookup"><span data-stu-id="7cdae-112">Description</span></span>  
 <span data-ttu-id="7cdae-113">このイベントは、`FaultProvider` が呼び出された後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="7cdae-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7cdae-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7cdae-114">Message</span></span>  
 <span data-ttu-id="7cdae-115">ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="7cdae-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7cdae-116">詳細</span><span class="sxs-lookup"><span data-stu-id="7cdae-116">Details</span></span>  
  
|<span data-ttu-id="7cdae-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7cdae-117">Data Item Name</span></span>|<span data-ttu-id="7cdae-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7cdae-118">Data Item Type</span></span>|<span data-ttu-id="7cdae-119">説明</span><span class="sxs-lookup"><span data-stu-id="7cdae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7cdae-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="7cdae-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="7cdae-121">呼び出された `FaultProvider` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="7cdae-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="7cdae-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="7cdae-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="7cdae-123">`FaultProvider` の操作対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="7cdae-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="7cdae-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="7cdae-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="7cdae-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="7cdae-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7cdae-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="7cdae-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7cdae-127">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="7cdae-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7cdae-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7cdae-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7cdae-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7cdae-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
