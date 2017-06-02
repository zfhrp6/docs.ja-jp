---
title: "方法: Probe 要求の探索バージョンを特定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法: Probe 要求の探索バージョンを特定する
探索プロキシでは、異なる探索バージョンを使用する複数の探索エンドポイントを公開する場合があります。  プロキシでは、UDP マルチキャスト Probe 要求を受け取った場合、マルチキャスト抑制メッセージで応答する必要があります。  これを行うには、要求の探索バージョンを特定する必要があります。  
  
### Probe 要求の探索バージョンを特定するには  
  
1.  次のコードに示すように、Probe 要求に応答するメソッド \(<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> など\) で静的 <xref:System.ServiceModel.OperationContext.Current%2A> プロパティを使用して <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> を検索します。  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
  
    ```  
  
## 参照  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>   
 [探索プロキシの実装](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)   
 [探索プロキシのサンプル](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)