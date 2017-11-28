---
title: "操作パフォーマンス カウンター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="649bd-102">操作パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="649bd-102">Operation Performance Counters</span></span>
<span data-ttu-id="649bd-103">操作パフォーマンス カウンターは、パフォーマンス モニター (Perfmon.exe) を使用して表示した場合、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="649bd-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="649bd-104">それぞれの操作に個別のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="649bd-104">Each operation has an individual instance.</span></span> <span data-ttu-id="649bd-105">つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="649bd-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="649bd-106">オブジェクトのインスタンスには次のパターンの名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="649bd-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="649bd-107">このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="649bd-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="649bd-108">パフォーマンス カウンターのインスタンス名の長さには制限があります。</span><span class="sxs-lookup"><span data-stu-id="649bd-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="649bd-109">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] カウンターのインスタンス名の長さが最大長を超えると、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によってインスタンス名の一部はハッシュ値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="649bd-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="649bd-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="649bd-110">See Also</span></span>  
 [<span data-ttu-id="649bd-111">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="649bd-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
