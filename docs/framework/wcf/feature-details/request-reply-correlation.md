---
title: 要求/応答の相関関係
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497205"
---
# <a name="request-reply-correlation"></a>要求/応答の相関関係
要求-応答の相関関係を併用、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアを使用して、ワークフロー サービスでは、双方向の操作を実装する、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペアを別の web サイトでの双方向の操作を呼び出すサービス。 WCF サービスの双方向の操作を呼び出すときに、サービスが、従来なることができるまたは命令型コードに基づく Windows Communication Foundation (WCF) サービスがワークフロー サービスを指定できます。 要求/応答の相関関係を使用するには、<xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドを使用する必要があります。 双方向の操作を呼び出す場合と実装する場合では、相関関係の初期化に同様の手順が使用されます。これらの手順については、このセクションで説明します。  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Receive/SendReply による双方向の操作での相関関係の使用  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアは、ワークフロー サービスに双方向の操作を実装するために使用します。 ランタイムは、要求/応答の相関関係を使用して、応答が正しい呼び出し元にディスパッチされるようにします。 ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合、つまり、ワークフロー サービスの場合は、既定の相関関係の初期化で十分です。 このシナリオでは、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアは、ワークフローで使用して、特定の相関関係の構成は必要ありません。  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>要求/応答の相関関係の明示的な初期化  
 他の双方向の操作が並列実行される場合、相関関係を明示的に構成する必要があります。 指定することによってこれ行う、<xref:System.ServiceModel.Activities.CorrelationHandle>と<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>、または配置することによって、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>の内側、<xref:System.ServiceModel.Activities.CorrelationScope>です。 この例では要求-応答の相関関係が構成されている、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペア。  
  
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
  
 相関関係を明示的に構成する代わりに、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティを使用することもできます。 <xref:System.ServiceModel.Activities.CorrelationScope> は、内包しているメッセージング アクティビティに暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> を提供します。 この例では、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアに含まれている、<xref:System.ServiceModel.Activities.CorrelationScope>です。 明示的な相関関係の構成は不要です。  
  
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
  
 追加の相関関係が必要な場合は、目的の種類の <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> を使用する各メッセージング アクティビティの `CorrelationInitializer` プロパティを使用して、追加の相関関係を構成します。  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Send/ReceiveReply による双方向の操作での相関関係の使用  
 中に、<xref:System.ServiceModel.Activities.Receive>アクティビティは、によってホストされるワークフロー サービスでのみ使用できます<xref:System.ServiceModel.Activities.WorkflowServiceHost>、<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペアは、Web サービスに対してメソッドを呼び出す必要のあるすべてのワークフローで使用できます。 ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされる場合は、前のセクションで説明した既定の相関関係が適用されますが、そうでない場合は、目的の <xref:System.ServiceModel.Activities.CorrelationInitializer> と <xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に使用するか、<xref:System.ServiceModel.Activities.CorrelationScope> による暗黙の処理管理を使用して、相関関係を構成する必要があります。  
  
 使用する場合**サービス参照の追加**アクティビティを生成する双方向の操作で、サービスでラップする、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペア要求/応答の相関関係で内部的にアクティビティを明示的に指定します。
