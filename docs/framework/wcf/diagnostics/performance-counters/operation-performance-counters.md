---
title: 操作パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 46b7d5ff071ebf1e3f790a9b56906d9908028ae9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804418"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="fa59e-102">操作パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="fa59e-102">Operation Performance Counters</span></span>
<span data-ttu-id="fa59e-103">操作パフォーマンス カウンターは、パフォーマンス モニター (Perfmon.exe) を使用して表示した場合、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="fa59e-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="fa59e-104">それぞれの操作に個別のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="fa59e-104">Each operation has an individual instance.</span></span> <span data-ttu-id="fa59e-105">つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="fa59e-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="fa59e-106">オブジェクトのインスタンスには次のパターンの名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="fa59e-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="fa59e-107">このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="fa59e-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fa59e-108">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="fa59e-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="fa59e-109">Windows Communication Foundation (WCF) カウンターのインスタンス名が最大長を超えると WCF では、ハッシュ値を持つのインスタンス名の一部が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="fa59e-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa59e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa59e-110">See Also</span></span>  
 [<span data-ttu-id="fa59e-111">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="fa59e-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
