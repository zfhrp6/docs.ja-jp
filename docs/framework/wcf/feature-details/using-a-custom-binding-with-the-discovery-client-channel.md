---
title: カスタム バインドを探索クライアント チャネルと共に使用する
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a5c80a257efb5f6006a0cf6394a1079cf92d2471
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>カスタム バインドを探索クライアント チャネルと共に使用する
カスタム バインディングを <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> と共に使用する場合は、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> インスタンスを作成する <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> を定義する必要があります。  
  
## <a name="creating-a-discoveryendpointprovider"></a>DiscoveryEndpointProvider の作成  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>の作成を担当<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>オンデマンド インスタンス。 探索エンドポイント プロバイダーを定義するには、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> からクラスを派生させ、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> メソッドをオーバーライドし、新しい探索エンドポイントを返します。 次の例は、探索エンドポイント プロバイダーを作成する方法を示しています。  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel   
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 探索エンドポイント プロバイダーを定義したら、次の例に示すように、カスタム バインディングを作成し、その探索エンドポイント プロバイダーを参照する <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> を追加できます。  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 詳細については、探索クライアント チャネルを使用して、次を参照してください。[探索クライアント チャネルを使用して](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)です。 完全なコード例は、次を参照してください[探索バインド要素のサンプル。](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)  
  
## <a name="see-also"></a>関連項目  
 [WCF Discovery の概要](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [探索クライアント チャネルの使用](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [探索バインド要素のサンプル](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
