---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514570"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="e6db2-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="e6db2-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="e6db2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e6db2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6db2-104">ID</span><span class="sxs-lookup"><span data-stu-id="e6db2-104">ID</span></span>|<span data-ttu-id="e6db2-105">4211</span><span class="sxs-lookup"><span data-stu-id="e6db2-105">4211</span></span>|  
|<span data-ttu-id="e6db2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e6db2-106">Keywords</span></span>|<span data-ttu-id="e6db2-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="e6db2-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="e6db2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e6db2-108">Level</span></span>|<span data-ttu-id="e6db2-109">警告</span><span class="sxs-lookup"><span data-stu-id="e6db2-109">Warning</span></span>|  
|<span data-ttu-id="e6db2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e6db2-110">Channel</span></span>|<span data-ttu-id="e6db2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e6db2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e6db2-112">説明</span><span class="sxs-lookup"><span data-stu-id="e6db2-112">Description</span></span>  
 <span data-ttu-id="e6db2-113">SQL の再試行をキューに登録していることを示します。</span><span class="sxs-lookup"><span data-stu-id="e6db2-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e6db2-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e6db2-114">Message</span></span>  
 <span data-ttu-id="e6db2-115">%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。</span><span class="sxs-lookup"><span data-stu-id="e6db2-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e6db2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e6db2-116">Details</span></span>  
  
|<span data-ttu-id="e6db2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e6db2-117">Data Item Name</span></span>|<span data-ttu-id="e6db2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e6db2-118">Data Item Type</span></span>|<span data-ttu-id="e6db2-119">説明</span><span class="sxs-lookup"><span data-stu-id="e6db2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e6db2-120">Delay</span><span class="sxs-lookup"><span data-stu-id="e6db2-120">Delay</span></span>|<span data-ttu-id="e6db2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6db2-121">xs:string</span></span>|<span data-ttu-id="e6db2-122">再試行の遅延。</span><span class="sxs-lookup"><span data-stu-id="e6db2-122">The delay between retries.</span></span>|  
|<span data-ttu-id="e6db2-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e6db2-123">AppDomain</span></span>|<span data-ttu-id="e6db2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6db2-124">xs:string</span></span>|<span data-ttu-id="e6db2-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e6db2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
