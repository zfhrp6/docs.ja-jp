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
# <a name="service-performance-counters"></a>サービス パフォーマンス カウンター
サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。 パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターのインスタンス名が最大長を超えると WCF では、ハッシュ値を持つのインスタンス名の一部が置き換えられます。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
