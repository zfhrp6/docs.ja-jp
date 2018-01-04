---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="891cd-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="891cd-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="891cd-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="891cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="891cd-104">ID</span><span class="sxs-lookup"><span data-stu-id="891cd-104">ID</span></span>|<span data-ttu-id="891cd-105">4211</span><span class="sxs-lookup"><span data-stu-id="891cd-105">4211</span></span>|  
|<span data-ttu-id="891cd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="891cd-106">Keywords</span></span>|<span data-ttu-id="891cd-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="891cd-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="891cd-108">レベル</span><span class="sxs-lookup"><span data-stu-id="891cd-108">Level</span></span>|<span data-ttu-id="891cd-109">警告</span><span class="sxs-lookup"><span data-stu-id="891cd-109">Warning</span></span>|  
|<span data-ttu-id="891cd-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="891cd-110">Channel</span></span>|<span data-ttu-id="891cd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="891cd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="891cd-112">説明</span><span class="sxs-lookup"><span data-stu-id="891cd-112">Description</span></span>  
 <span data-ttu-id="891cd-113">SQL の再試行をキューに登録していることを示します。</span><span class="sxs-lookup"><span data-stu-id="891cd-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="891cd-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="891cd-114">Message</span></span>  
 <span data-ttu-id="891cd-115">%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。</span><span class="sxs-lookup"><span data-stu-id="891cd-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="891cd-116">詳細</span><span class="sxs-lookup"><span data-stu-id="891cd-116">Details</span></span>  
  
|<span data-ttu-id="891cd-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="891cd-117">Data Item Name</span></span>|<span data-ttu-id="891cd-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="891cd-118">Data Item Type</span></span>|<span data-ttu-id="891cd-119">説明</span><span class="sxs-lookup"><span data-stu-id="891cd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="891cd-120">Delay</span><span class="sxs-lookup"><span data-stu-id="891cd-120">Delay</span></span>|<span data-ttu-id="891cd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="891cd-121">xs:string</span></span>|<span data-ttu-id="891cd-122">再試行の遅延。</span><span class="sxs-lookup"><span data-stu-id="891cd-122">The delay between retries.</span></span>|  
|<span data-ttu-id="891cd-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="891cd-123">AppDomain</span></span>|<span data-ttu-id="891cd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="891cd-124">xs:string</span></span>|<span data-ttu-id="891cd-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="891cd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
