---
title: 呼び出す期間
ms.date: 03/30/2017
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
ms.openlocfilehash: df361774373d08ad6e9e027314c0529ea97d6b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472854"
---
# <a name="call-duration"></a><span data-ttu-id="0f04d-102">呼び出す期間</span><span class="sxs-lookup"><span data-stu-id="0f04d-102">Call Duration</span></span>
<span data-ttu-id="0f04d-103">カウンター名 : 呼び出す期間</span><span class="sxs-lookup"><span data-stu-id="0f04d-103">Counter Name: Call Duration</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f04d-104">説明</span><span class="sxs-lookup"><span data-stu-id="0f04d-104">Description</span></span>  
 <span data-ttu-id="0f04d-105">この操作の呼び出しの平均期間です。</span><span class="sxs-lookup"><span data-stu-id="0f04d-105">The average duration of calls to this operation.</span></span> <span data-ttu-id="0f04d-106">平均期間は、(N1-N0)/(D1-D0) という数式に基づいて計算されます。</span><span class="sxs-lookup"><span data-stu-id="0f04d-106">The average duration is calculated based on this equation: (N1-N0)/(D1-D0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0f04d-107">非同期の WCF サービス上で使用される場合、呼び出す期間カウンターは常に -1 を返します。</span><span class="sxs-lookup"><span data-stu-id="0f04d-107">When used on an asynchronous WCF service the Call Duration counter will always return -1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f04d-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f04d-108">See Also</span></span>  
 [<span data-ttu-id="0f04d-109">PERF_AVERAGE_TIMER</span><span class="sxs-lookup"><span data-stu-id="0f04d-109">PERF_AVERAGE_TIMER</span></span>](http://go.microsoft.com/fwlink/?LinkId=95015)
