---
title: '方法: Probe 要求の探索バージョンを特定する'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8ac9804b0fe46ca5fbe580d713ec82a2f9bb0128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>方法: Probe 要求の探索バージョンを特定する
探索プロキシでは、異なる探索バージョンを使用する複数の探索エンドポイントを公開する場合があります。 プロキシでは、UDP マルチキャスト Probe 要求を受け取った場合、マルチキャスト抑制メッセージで応答する必要があります。 これを行うには、要求の探索バージョンを特定する必要があります。  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Probe 要求の探索バージョンを特定するには  
  
1.  次のコードに示すように、Probe 要求に応答するメソッド (<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> など) で静的 <xref:System.ServiceModel.OperationContext.Current%2A> プロパティを使用して <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> を検索します。  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [探索プロキシの実装](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [探索プロキシのサンプル](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
