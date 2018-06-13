---
title: サービス パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bdc68fd2b629c538c097dab4e1cf3f89b7f3a091
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810188"
---
# <a name="service-performance-counters"></a><span data-ttu-id="86d1e-102">サービス パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="86d1e-102">Service Performance Counters</span></span>
<span data-ttu-id="86d1e-103">サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="86d1e-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="86d1e-104">パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="86d1e-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="86d1e-105">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="86d1e-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="86d1e-106">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="86d1e-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="86d1e-107">Windows Communication Foundation (WCF) カウンターのインスタンス名が最大長を超えると WCF では、ハッシュ値を持つのインスタンス名の一部が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="86d1e-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d1e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="86d1e-108">See Also</span></span>  
 [<span data-ttu-id="86d1e-109">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="86d1e-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
