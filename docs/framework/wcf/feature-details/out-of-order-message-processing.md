---
title: "順番を無視したメッセージの処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffd220babe99661d8b6aaf271a566d415af5eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="66bdc-102">順番を無視したメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="66bdc-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="66bdc-103">ワークフロー サービスは、特定の順序で送信されるメッセージに依存する場合があります。</span><span class="sxs-lookup"><span data-stu-id="66bdc-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="66bdc-104">ワークフロー サービスには 1 つ以上の <xref:System.ServiceModel.Activities.Receive> アクティビティが含まれ、それぞれの <xref:System.ServiceModel.Activities.Receive> アクティビティは特定のメッセージに対応しています。</span><span class="sxs-lookup"><span data-stu-id="66bdc-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="66bdc-105">特定のトランスポート配信保証がないと、クライアントから送信されるメッセージに遅延が生じ、それによって、ワークフロー サービスが予期しない順序でメッセージが配信されることがあります。</span><span class="sxs-lookup"><span data-stu-id="66bdc-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="66bdc-106">特定の順序でメッセージが送信されることを必要としないワークフローは、通常、Parallel アクティビティを使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="66bdc-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="66bdc-107">アプリケーション プロトコルがより複雑な場合は、ワークフローがすぐに複雑になります。</span><span class="sxs-lookup"><span data-stu-id="66bdc-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="66bdc-108">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメッセージ処理機能では、順番が無視されるため、入れ子になった複雑な Parallel アクティビティを含まないワークフローを作成できます。</span><span class="sxs-lookup"><span data-stu-id="66bdc-108">The out-of-order message processing feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="66bdc-109">順番を無視したメッセージ処理は、<xref:System.ServiceModel.Channels.ReceiveContext> MSMQ バインディングなど、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に対応するチャネルでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="66bdc-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="66bdc-110">順番を無視したメッセージ処理の有効化</span><span class="sxs-lookup"><span data-stu-id="66bdc-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="66bdc-111">順番を無視したメッセージ処理は、ワークフロー サービスで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを `true` に設定することで有効化できます。</span><span class="sxs-lookup"><span data-stu-id="66bdc-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="66bdc-112">次の例は、コードで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="66bdc-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="66bdc-113">また、次の例に示すように、XAML で `AllowBufferedReceive` 属性をワークフロー サービスに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="66bdc-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66bdc-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="66bdc-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="66bdc-115">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="66bdc-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="66bdc-116">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="66bdc-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
