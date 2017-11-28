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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c318ee6509ce8b96a1e7e78a13f4aeb7c76dde6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="6ee58-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="6ee58-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="6ee58-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6ee58-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ee58-104">ID</span><span class="sxs-lookup"><span data-stu-id="6ee58-104">ID</span></span>|<span data-ttu-id="6ee58-105">4211</span><span class="sxs-lookup"><span data-stu-id="6ee58-105">4211</span></span>|  
|<span data-ttu-id="6ee58-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6ee58-106">Keywords</span></span>|<span data-ttu-id="6ee58-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="6ee58-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="6ee58-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6ee58-108">Level</span></span>|<span data-ttu-id="6ee58-109">警告</span><span class="sxs-lookup"><span data-stu-id="6ee58-109">Warning</span></span>|  
|<span data-ttu-id="6ee58-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6ee58-110">Channel</span></span>|<span data-ttu-id="6ee58-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6ee58-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6ee58-112">説明</span><span class="sxs-lookup"><span data-stu-id="6ee58-112">Description</span></span>  
 <span data-ttu-id="6ee58-113">SQL の再試行をキューに登録していることを示します。</span><span class="sxs-lookup"><span data-stu-id="6ee58-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6ee58-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6ee58-114">Message</span></span>  
 <span data-ttu-id="6ee58-115">%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。</span><span class="sxs-lookup"><span data-stu-id="6ee58-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6ee58-116">詳細</span><span class="sxs-lookup"><span data-stu-id="6ee58-116">Details</span></span>  
  
|<span data-ttu-id="6ee58-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6ee58-117">Data Item Name</span></span>|<span data-ttu-id="6ee58-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6ee58-118">Data Item Type</span></span>|<span data-ttu-id="6ee58-119">説明</span><span class="sxs-lookup"><span data-stu-id="6ee58-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6ee58-120">Delay</span><span class="sxs-lookup"><span data-stu-id="6ee58-120">Delay</span></span>|<span data-ttu-id="6ee58-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ee58-121">xs:string</span></span>|<span data-ttu-id="6ee58-122">再試行の遅延。</span><span class="sxs-lookup"><span data-stu-id="6ee58-122">The delay between retries.</span></span>|  
|<span data-ttu-id="6ee58-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6ee58-123">AppDomain</span></span>|<span data-ttu-id="6ee58-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ee58-124">xs:string</span></span>|<span data-ttu-id="6ee58-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6ee58-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
