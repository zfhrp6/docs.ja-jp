---
title: 1 秒あたりの呼び出し回数
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 04eb5deaf8e6eb09be4e0bf404bec11b8ce84427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472620"
---
# <a name="calls-per-second"></a><span data-ttu-id="b8d6e-102">1 秒あたりの呼び出し回数</span><span class="sxs-lookup"><span data-stu-id="b8d6e-102">Calls Per Second</span></span>
<span data-ttu-id="b8d6e-103">カウンター名 : 1 秒あたりの呼び出し回数</span><span class="sxs-lookup"><span data-stu-id="b8d6e-103">Counter Name: Calls Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b8d6e-104">説明</span><span class="sxs-lookup"><span data-stu-id="b8d6e-104">Description</span></span>  
 <span data-ttu-id="b8d6e-105">この操作が 1 秒あたりに呼び出される回数です。</span><span class="sxs-lookup"><span data-stu-id="b8d6e-105">Number of calls to this operation in a second.</span></span>  
  
 <span data-ttu-id="b8d6e-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="b8d6e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b8d6e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b8d6e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
