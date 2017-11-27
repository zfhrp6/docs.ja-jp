---
title: "サービス パフォーマンス カウンター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: de51c6d0a3070f8bba8a2c77f9c028e7cfbc944d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-performance-counters"></a><span data-ttu-id="e46ae-102">サービス パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="e46ae-102">Service Performance Counters</span></span>
<span data-ttu-id="e46ae-103">サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="e46ae-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="e46ae-104">パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="e46ae-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="e46ae-105">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="e46ae-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="e46ae-106">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="e46ae-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="e46ae-107">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] カウンターのインスタンス名の長さが最大長を超えると、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によってインスタンス名の一部はハッシュ値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e46ae-107">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46ae-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e46ae-108">See Also</span></span>  
 [<span data-ttu-id="e46ae-109">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="e46ae-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
