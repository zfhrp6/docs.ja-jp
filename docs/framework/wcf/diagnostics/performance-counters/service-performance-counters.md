---
title: サービス パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 71eff5c656a4782056ac518f105f73bc549da336
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="service-performance-counters"></a>サービス パフォーマンス カウンター
サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。 パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターのインスタンス名は、最大の長さを超えているときに[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]インスタンス名の一部をハッシュ値に置き換えます。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
