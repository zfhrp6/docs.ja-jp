---
title: "順番を無視したメッセージの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 順番を無視したメッセージの処理
ワークフロー サービスは、特定の順序で送信されるメッセージに依存する場合があります。ワークフロー サービスには 1 つ以上の <xref:System.ServiceModel.Activities.Receive> アクティビティが含まれ、それぞれの <xref:System.ServiceModel.Activities.Receive> アクティビティは特定のメッセージに対応しています。特定のトランスポート配信保証がないと、クライアントから送信されるメッセージに遅延が生じ、それによって、ワークフロー サービスが予期しない順序でメッセージが配信されることがあります。特定の順序でメッセージが送信されることを必要としないワークフローは、通常、Parallel アクティビティを使用して実装されます。アプリケーション プロトコルがより複雑な場合は、ワークフローがすぐに複雑になります。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメッセージ処理機能では、順番が無視されるため、入れ子になった複雑な Parallel アクティビティを含まないワークフローを作成できます。順番を無視したメッセージ処理は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ バインディングなど、<xref:System.ServiceModel.Channele.ReceiveContext> に対応するチャネルでのみサポートされます。  
  
## 順番を無視したメッセージ処理の有効化  
 順番を無視したメッセージ処理は、ワークフロー サービスで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを `true` に設定することで有効化できます。次の例は、コードで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを設定する方法を示しています。  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
  
```  
  
 また、次の例に示すように、XAML で `AllowBufferedReceive` 属性をワークフロー サービスに適用することもできます。  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## 参照  
 <xref:System.ServiceModel.Channels.ReceiveContext>   
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)