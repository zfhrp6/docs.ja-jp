---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1034ae6bd6072a3849d72fafcad55c61e500439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="e93c1-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="e93c1-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="e93c1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e93c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e93c1-104">ID</span><span class="sxs-lookup"><span data-stu-id="e93c1-104">ID</span></span>|<span data-ttu-id="e93c1-105">499</span><span class="sxs-lookup"><span data-stu-id="e93c1-105">499</span></span>|  
|<span data-ttu-id="e93c1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e93c1-106">Keywords</span></span>|<span data-ttu-id="e93c1-107">Troubleshooting、UserEvents、EndToEndMonitoring、ServiceModel、WFTracking、ServiceHost、WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="e93c1-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="e93c1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e93c1-108">Level</span></span>|<span data-ttu-id="e93c1-109">LogAlways (常にログ)</span><span class="sxs-lookup"><span data-stu-id="e93c1-109">LogAlways</span></span>|  
|<span data-ttu-id="e93c1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e93c1-110">Channel</span></span>|<span data-ttu-id="e93c1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e93c1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e93c1-112">説明</span><span class="sxs-lookup"><span data-stu-id="e93c1-112">Description</span></span>  
 <span data-ttu-id="e93c1-113">このイベントは、転送イベントが発生したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="e93c1-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e93c1-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e93c1-114">Message</span></span>  
 <span data-ttu-id="e93c1-115">転送イベントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="e93c1-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e93c1-116">説明</span><span class="sxs-lookup"><span data-stu-id="e93c1-116">Details</span></span>  
  
|<span data-ttu-id="e93c1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e93c1-117">Data Item Name</span></span>|<span data-ttu-id="e93c1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e93c1-118">Data Item Type</span></span>|<span data-ttu-id="e93c1-119">説明</span><span class="sxs-lookup"><span data-stu-id="e93c1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e93c1-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="e93c1-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="e93c1-121">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="e93c1-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e93c1-122">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="e93c1-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e93c1-123">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="e93c1-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e93c1-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e93c1-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e93c1-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e93c1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
