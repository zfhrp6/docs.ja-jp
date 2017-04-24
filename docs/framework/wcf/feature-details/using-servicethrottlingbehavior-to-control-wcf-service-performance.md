---
title: "WCF サービス パフォーマンスを制御するための ServiceThrottlingBehavior の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービスのパフォーマンスの動作 [WCF]"
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# WCF サービス パフォーマンスを制御するための ServiceThrottlingBehavior の使用
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>クラス インスタンスの数を制限するために使用できるか、セッションは、アプリケーション レベルで作成するプロパティを公開します。 この動作を使用して、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションのパフォーマンスを最適に調整できます。  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>サービス インスタンスと同時呼び出しの制御  
 使用して、 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>でアクティブに処理されるメッセージの最大数を指定するプロパティ、 <xref:System.ServiceModel.ServiceHost>クラス、および<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>の最大数を指定するプロパティ<xref:System.ServiceModel.InstanceContext>サービス内のオブジェクト。  
  
 通常、これらのプロパティ設定の決定はに対してアプリケーションを実行している実際の動作後に行われるのための設定を読み込みます、 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>プロパティは、通常、アプリケーション構成ファイルを使用して指定、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)要素。  
  
 次のコード例の使用を示しています、 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>を設定するアプリケーション構成ファイルからクラスを<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>、 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>、および<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>プロパティを 1 に簡単な例として。 特定のアプリケーションでの最適な設定については、実際の動作から判断します。  
  
 <!-- TODO: review snippet reference [!code-csharp[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  -->  
  
 値によって、実際の実行時動作、 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>と<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>プロパティは、メッセージの数が、操作内実行できる同時やサービスの有効期間<xref:System.ServiceModel.InstanceContext>受信チャネル セッションに関連、それぞれします。  
  
 詳細については、「 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>、および<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>   
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>