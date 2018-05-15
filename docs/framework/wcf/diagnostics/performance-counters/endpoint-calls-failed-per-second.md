---
title: 'エンドポイント: 1 秒あたりの失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: c0273fc90ad5702663862612f52f03c42f410b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="88aa6-102">エンドポイント: 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="88aa6-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="88aa6-103">カウンター名 : 1 秒あたりの失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="88aa6-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88aa6-104">説明</span><span class="sxs-lookup"><span data-stu-id="88aa6-104">Description</span></span>  
 <span data-ttu-id="88aa6-105">未処理の例外を伴ってこのエンドポイントに到達した、1 秒あたりの呼び出しの回数。</span><span class="sxs-lookup"><span data-stu-id="88aa6-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="88aa6-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="88aa6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="88aa6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="88aa6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="88aa6-108">このカウンターは、このエンドポイントで未処理の例外が発生すると常にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="88aa6-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88aa6-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="88aa6-109">See Also</span></span>  
 [<span data-ttu-id="88aa6-110">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="88aa6-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
