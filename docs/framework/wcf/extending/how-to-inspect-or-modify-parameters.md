---
title: "方法 : パラメーターを検査または変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : パラメーターを検査または変更する
検査またはに&1; 回の操作の受信または送信メッセージを変更することができます、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]クライアント オブジェクトまたは[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]実装することによってサービス、 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>インターフェイスとそれをクライアントまたはサービス ランタイムに挿入します。 通常、操作の動作は、1 回の操作に対してパラメーター インスペクターを追加するために使用します。他の動作は、広い範囲でランタイムへの簡単なアクセスを提供するために使用できます。 詳細については、次を参照してください。[を拡張するクライアント](../../../../docs/framework/wcf/extending/extending-clients.md)と[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)します。  
  
### <a name="inspecting-or-modifying-parameters"></a>パラメーターの検査と変更  
  
1.  実装、 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>インターフェイスです。  
  
2.  実装、 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>、 <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>、 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>または<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName>(要求されるスコープに応じて) するか、パラメーター インスペクターを追加する、 <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=fullName>または<xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=fullName>プロパティです。  
  
3.  呼び出しの前に、動作を挿入<xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=fullName>または<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName>メソッドを<xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>します。 詳細については、「[の構成と動作を使用したランタイムの拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)します。  
  
## <a name="example"></a>例  
 下のコード例では、次の項目を順番に示しています。  
  
-   パラメーター インスペクターの実装  
  
-   使用してパラメーター インスペクターを挿入する動作実装、 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>、 <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>、および<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>します。  
  
-   クライアント上にパラメーター インスペクターを挿入するために、クライアント アプリケーションでエンドポイント動作を読み込み、実行する構成ファイル  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 <!-- TODO: review snippet reference [!code[Interceptors#3](../../../../samples/snippets/common/VS_Snippets_CFX/interceptors/common/client.exe.config#3)]  -->
 <!-- TODO: review snippet reference [!code-csharp[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  -->
 <!-- TODO: review snippet reference [!code-vb[Interceptors#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/client.exe.config#3)]  -->  
  
## <a name="see-also"></a>関連項目  
 [構成と動作を使用したランタイムの拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)