---
title: "軽減策: minFreeMemoryPercentageToActiveService 構成の設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 軽減策: minFreeMemoryPercentageToActiveService 構成の設定
[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] では、Web サーバーの使用可能なメモリが [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 構成設定で指定されたパーセンテージより小さい場合に例外がスローされます。  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、この設定は無視されます。  
  
## 影響  
 ほとんどの場合、[minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定に従うことによる影響は望ましいものです。制約されたメモリを持つシステムで Windows Communication Foundation \(WCF\) サービスが開始されるときに発生する可能性のある <xref:System.OutOfMemoryException> 例外を防ぐことによってシステムの安定性が向上します。  
  
 ただし、以前は正常に開始されたサービスが起動できない場合があります。  その場合、詳細なエラー メッセージが表示されます。  
  
```Output  
  
空きメモリ (nnnn バイト) が総メモリの nn% 未満であるため、メモリ ゲートの確認は失敗しました。  その結果、サービスは受け取る要求に使用できません。  これを解決するには、マシンの負荷を減らすか、serviceHostingEnvironment 構成要素の minFreeMemoryPercentageToActivateService の値を調整します。    
```  
  
## 軽減策  
 [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定が無視された、前の動作に戻すには、次に示すように web.config ファイルを変更します。  
  
```  
  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
  
```  
  
## 参照  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)