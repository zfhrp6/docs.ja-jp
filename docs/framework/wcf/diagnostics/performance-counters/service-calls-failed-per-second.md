---
title: "サービス : 1 秒あたりの失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2072a686d5d424f90ac2f32cf5fc11564b07542c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="bcc1f-102">サービス : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="bcc1f-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="bcc1f-103">カウンター名 : 1 秒あたりの失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="bcc1f-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bcc1f-104">説明</span><span class="sxs-lookup"><span data-stu-id="bcc1f-104">Description</span></span>  
 <span data-ttu-id="bcc1f-105">このサービスが 1 秒間に受信した未処理の例外を含む呼び出しの回数。</span><span class="sxs-lookup"><span data-stu-id="bcc1f-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="bcc1f-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="bcc1f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bcc1f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="bcc1f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="bcc1f-108">マネージ コードでは、エラー条件が発生すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bcc1f-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="bcc1f-109">マネージ コードでは、エラー条件が発生すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bcc1f-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="bcc1f-110">このカウンターは、このサービスで未処理の例外が発生するたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="bcc1f-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc1f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcc1f-111">See Also</span></span>  
 [<span data-ttu-id="bcc1f-112">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="bcc1f-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
