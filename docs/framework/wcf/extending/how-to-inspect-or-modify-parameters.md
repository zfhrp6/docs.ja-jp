---
title: '方法 : パラメーターを検査または変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 1b825ff795f4db9d570420b187b8fedd041ddd3d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809954"
---
# <a name="how-to-inspect-or-modify-parameters"></a>方法 : パラメーターを検査または変更する
検査または実装することによって、Windows Communication Foundation (WCF) クライアント オブジェクトまたは WCF サービスの単一操作による受信または送信メッセージを変更することができます、<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>インターフェイスと、クライアントまたはサービス ランタイムに挿入します。 通常、操作の動作は、1 回の操作に対してパラメーター インスペクターを追加するために使用します。他の動作は、広い範囲でランタイムへの簡単なアクセスを提供するために使用できます。 詳細については、次を参照してください。[を拡張するクライアント](../../../../docs/framework/wcf/extending/extending-clients.md)と[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)です。  
  
### <a name="inspecting-or-modifying-parameters"></a>パラメーターの検査と変更  
  
1.  <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> インターフェイスを実装します。  
  
2.  要求されるスコープに応じて <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> を実装し、パラメーター インスペクターを <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> プロパティに追加します。  
  
3.  <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> に対して <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> メソッドまたは <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。 詳細については、「[を構成して、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。  
  
## <a name="example"></a>例  
 下のコード例では、次の項目を順番に示しています。  
  
-   パラメーター インスペクターの実装  
  
-   <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、および <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> を使用してパラメーター インスペクターを挿入する動作実装  
  
-   クライアント上にパラメーター インスペクターを挿入するために、クライアント アプリケーションでエンドポイント動作を読み込み、実行する構成ファイル  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>関連項目  
 [動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
