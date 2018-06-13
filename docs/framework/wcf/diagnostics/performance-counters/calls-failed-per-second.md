---
title: 1 秒あたりの失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 19f09b2a2132cab56da5dec49bdc8d5f5e4c8b8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474455"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="9f4e1-102">1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="9f4e1-102">Calls Failed Per Second</span></span>
<span data-ttu-id="9f4e1-103">カウンター名 : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="9f4e1-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f4e1-104">説明</span><span class="sxs-lookup"><span data-stu-id="9f4e1-104">Description</span></span>  
 <span data-ttu-id="9f4e1-105">1 秒間にこの操作で未処理の例外が発生した呼び出しの回数です。</span><span class="sxs-lookup"><span data-stu-id="9f4e1-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="9f4e1-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="9f4e1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9f4e1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9f4e1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="9f4e1-108">このカウンターは、この操作で未処理の例外が発生するたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="9f4e1-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f4e1-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f4e1-109">See Also</span></span>  
 [<span data-ttu-id="9f4e1-110">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="9f4e1-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
