---
title: "呼び出す期間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9bf221115b7919a1ca7facdfe80af2af899b3326
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="call-duration"></a><span data-ttu-id="d89ce-102">呼び出す期間</span><span class="sxs-lookup"><span data-stu-id="d89ce-102">Call Duration</span></span>
<span data-ttu-id="d89ce-103">カウンター名 : 呼び出す期間</span><span class="sxs-lookup"><span data-stu-id="d89ce-103">Counter Name: Call Duration</span></span>  
  
## <a name="description"></a><span data-ttu-id="d89ce-104">説明</span><span class="sxs-lookup"><span data-stu-id="d89ce-104">Description</span></span>  
 <span data-ttu-id="d89ce-105">この操作の呼び出しの平均期間です。</span><span class="sxs-lookup"><span data-stu-id="d89ce-105">The average duration of calls to this operation.</span></span> <span data-ttu-id="d89ce-106">平均期間は、(N1-N0)/(D1-D0) という数式に基づいて計算されます。</span><span class="sxs-lookup"><span data-stu-id="d89ce-106">The average duration is calculated based on this equation: (N1-N0)/(D1-D0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d89ce-107">非同期の WCF サービス上で使用される場合、呼び出す期間カウンターは常に -1 を返します。</span><span class="sxs-lookup"><span data-stu-id="d89ce-107">When used on an asynchronous WCF service the Call Duration counter will always return -1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89ce-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="d89ce-108">See Also</span></span>  
 [<span data-ttu-id="d89ce-109">PERF_AVERAGE_TIMER</span><span class="sxs-lookup"><span data-stu-id="d89ce-109">PERF_AVERAGE_TIMER</span></span>](http://go.microsoft.com/fwlink/?LinkId=95015)
