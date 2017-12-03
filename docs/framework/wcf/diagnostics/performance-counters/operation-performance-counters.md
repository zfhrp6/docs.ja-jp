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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c752c56fa60cd717f54a7a06d0d3be8b70e7772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="operation-performance-counters"></a>操作パフォーマンス カウンター
操作パフォーマンス カウンターは、パフォーマンス モニター (Perfmon.exe) を使用して表示した場合、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。 それぞれの操作に個別のインスタンスがあります。 つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。 オブジェクトのインスタンスには次のパターンの名前が付いています。  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。  
  
> [!CAUTION]
>  パフォーマンス カウンターのインスタンス名の長さには制限があります。 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] カウンターのインスタンス名の長さが最大長を超えると、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によってインスタンス名の一部はハッシュ値に置き換えられます。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
