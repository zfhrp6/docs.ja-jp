---
title: "要求/応答の相関関係 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 要求/応答の相関関係
要求\/応答の相関関係は、<xref:System.ServiceModel.Activities.ReceiveReply> と <xref:System.ServiceModel.Activities.Send> のペアと使用すると、ワークフロー サービスに双方向の操作を実装でき、<xref:System.ServiceModel.Activities.SendReply> と <xref:System.ServiceModel.Activities.Receive> のペアと使用すると、別の Web サービスの双方向の操作を呼び出すことができます。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの双方向の操作を呼び出す場合、このサービスには、従来の命令型のコード ベースの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを使用することも、ワークフロー サービスを使用することもできます。  要求\/応答の相関関係を使用するには、<xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドを使用する必要があります。  双方向の操作を呼び出す場合と実装する場合では、相関関係の初期化に同様の手順が使用されます。これらの手順については、このセクションで説明します。  
  
## Receive\/SendReply による双方向の操作での相関関係の使用  
 <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> のペアは、ワークフロー  サービスに双方向の操作を実装するために使用されます。  ランタイムは、要求\/応答の相関関係を使用して、応答が正しい呼び出し元にディスパッチされるようにします。  ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合、つまり、ワークフロー サービスの場合は、既定の相関関係の初期化で十分です。  このシナリオでは、<xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> のペアがワークフローによって使用されます。特定の相関関係の構成は不要です。  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
  
```  
  
### 要求\/応答の相関関係の明示的な初期化  
 他の双方向の操作が並列実行される場合、相関関係を明示的に構成する必要があります。  それには、<xref:System.ServiceModel.Activities.CorrelationHandle> と <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> を指定するか、<xref:System.ServiceModel.Activities.CorrelationScope> 内に <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> を設定します。  この例では、要求\/応答の相関関係が <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> のペアを使用して構成されています。  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 相関関係を明示的に構成する代わりに、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティを使用することもできます。  <xref:System.ServiceModel.Activities.CorrelationScope> は、内包しているメッセージング アクティビティに暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> を提供します。  この例では、<xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> ペアが <xref:System.ServiceModel.Activities.CorrelationScope> に内包されています。  明示的な相関関係の構成は不要です。  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =   
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 追加の相関関係が必要な場合は、目的の種類の `CorrelationInitializer` を使用する各メッセージング アクティビティの <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> プロパティを使用して、追加の相関関係を構成します。  
  
## Send\/ReceiveReply による双方向の操作での相関関係の使用  
 <xref:System.ServiceModel.Activities.Receive> アクティビティは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> によってホストされるワークフロー サービスでのみ使用できますが、<xref:System.ServiceModel.Activities.Send> および <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> のペアは、Web サービスに対してメソッドを呼び出す必要のあるすべてのワークフローで使用できます。  ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされる場合は、前のセクションで説明した既定の相関関係が適用されますが、そうでない場合は、目的の <xref:System.ServiceModel.Activities.CorrelationInitializer> と <xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に使用するか、<xref:System.ServiceModel.Activities.CorrelationScope> による暗黙の処理管理を使用して、相関関係を構成する必要があります。  
  
 双方向の操作があるサービスで **\[サービス参照の追加\]** を使用する場合は、明示的に指定された Request\/Reply 相関関係を使用して、内部に <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> ペア アクティビティをラップするアクティビティが生成されます。