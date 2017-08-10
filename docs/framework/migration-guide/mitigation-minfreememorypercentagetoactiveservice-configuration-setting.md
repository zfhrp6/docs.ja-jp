---
title: "軽減策: minFreeMemoryPercentageToActiveService 構成の設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7f228890476d45517a21bc09806538139c5e389
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-minfreememorypercentagetoactiveservice-configuration-setting"></a>軽減策: minFreeMemoryPercentageToActiveService 構成の設定
[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] では、Web サーバーの使用可能なメモリが [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 構成設定で指定されたパーセンテージより小さい場合に例外がスローされます。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、この設定は無視されます。  
  
## <a name="impact"></a>影響  
 ほとんどの場合、[minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定に従うことによる影響は望ましいものです。制約されたメモリを持つシステムで Windows Communication Foundation (WCF) サービスが開始されるときに発生する可能性のある <xref:System.OutOfMemoryException> 例外を防ぐことによってシステムの安定性が向上します。  
  
 ただし、以前は正常に開始されたサービスが起動できない場合があります。 その場合、詳細なエラー メッセージが表示されます。  
  
```console
Memory gates checking failed because the free memory (nnnn bytes) is less than nn% of total memory. As a result, the service will not be available for incoming requests. To resolve this, either reduce the load on the machine or adjust the value of minFreeMemoryPercentageToActivateService on the serviceHostingEnvironment config element.
```
  
## <a name="mitigation"></a>軽減策  
 [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定が無視された、前の動作に戻すには、次に示すように web.config ファイルを変更します。  
  
```xml
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

