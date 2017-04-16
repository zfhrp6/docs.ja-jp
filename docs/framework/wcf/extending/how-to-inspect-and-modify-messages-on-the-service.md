---
title: "方法 : サービスのメッセージを検査および変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 方法 : サービスのメッセージを検査および変更する
検査またはを介して受信または送信メッセージを変更できる、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]クライアントを実装することによって、 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>をサービス ランタイムに挿入します。 詳細については、次を参照してください。[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)します。 サービスの同等の機能は、 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>します。  
  
### <a name="to-inspect-or-modify-messages"></a>メッセージを検査または変更するには  
  
1.  実装、 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>インターフェイスです。  
  
2.  実装、 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>、 <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>、または<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName>インターフェイス サービス メッセージ インスペクターを容易に挿入するスコープによって異なります。  
  
3.  呼び出しの前に、動作を挿入、 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName>メソッドを<xref:System.ServiceModel.ServiceHost?displayProperty=fullName>します。 詳細については、「[の構成と動作を使用したランタイムの拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)します。  
  
## <a name="example"></a>例  
 下のコード例では、次の項目を順番に示しています。  
  
-   サービス インスペクターの実装  
  
-   インスペクターを挿入するサービス動作  
  
-   サービス アプリケーションに動作を読み込んで実行する構成ファイル  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code[Interceptors#9](../../../../samples/snippets/common/VS_Snippets_CFX/interceptors/common/hostapplication.exe.config#9)]
 [!code-csharp[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]
 [!code-vb[Interceptors#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>   
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>   
 [構成と動作を使用したランタイムの拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)