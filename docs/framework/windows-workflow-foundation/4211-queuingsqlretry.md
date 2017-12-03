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
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="ae8a1-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="ae8a1-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="ae8a1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ae8a1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae8a1-104">ID</span><span class="sxs-lookup"><span data-stu-id="ae8a1-104">ID</span></span>|<span data-ttu-id="ae8a1-105">4211</span><span class="sxs-lookup"><span data-stu-id="ae8a1-105">4211</span></span>|  
|<span data-ttu-id="ae8a1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ae8a1-106">Keywords</span></span>|<span data-ttu-id="ae8a1-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ae8a1-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ae8a1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ae8a1-108">Level</span></span>|<span data-ttu-id="ae8a1-109">警告</span><span class="sxs-lookup"><span data-stu-id="ae8a1-109">Warning</span></span>|  
|<span data-ttu-id="ae8a1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ae8a1-110">Channel</span></span>|<span data-ttu-id="ae8a1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ae8a1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae8a1-112">説明</span><span class="sxs-lookup"><span data-stu-id="ae8a1-112">Description</span></span>  
 <span data-ttu-id="ae8a1-113">SQL の再試行をキューに登録していることを示します。</span><span class="sxs-lookup"><span data-stu-id="ae8a1-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae8a1-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ae8a1-114">Message</span></span>  
 <span data-ttu-id="ae8a1-115">%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。</span><span class="sxs-lookup"><span data-stu-id="ae8a1-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae8a1-116">詳細</span><span class="sxs-lookup"><span data-stu-id="ae8a1-116">Details</span></span>  
  
|<span data-ttu-id="ae8a1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ae8a1-117">Data Item Name</span></span>|<span data-ttu-id="ae8a1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ae8a1-118">Data Item Type</span></span>|<span data-ttu-id="ae8a1-119">説明</span><span class="sxs-lookup"><span data-stu-id="ae8a1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae8a1-120">Delay</span><span class="sxs-lookup"><span data-stu-id="ae8a1-120">Delay</span></span>|<span data-ttu-id="ae8a1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae8a1-121">xs:string</span></span>|<span data-ttu-id="ae8a1-122">再試行の遅延。</span><span class="sxs-lookup"><span data-stu-id="ae8a1-122">The delay between retries.</span></span>|  
|<span data-ttu-id="ae8a1-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ae8a1-123">AppDomain</span></span>|<span data-ttu-id="ae8a1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae8a1-124">xs:string</span></span>|<span data-ttu-id="ae8a1-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ae8a1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
