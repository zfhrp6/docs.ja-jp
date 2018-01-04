---
title: "要求/応答の相関関係"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38f4fc436afbcc5922badda22e9a6e565bc19a0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="request-reply-correlation"></a><span data-ttu-id="9f886-102">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="9f886-102">Request-Reply Correlation</span></span>
<span data-ttu-id="9f886-103">要求-応答の相関関係を併用、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアを使用して、ワークフロー サービスでは、双方向の操作を実装する、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペアを別の web サイトでの双方向の操作を呼び出すサービス。</span><span class="sxs-lookup"><span data-stu-id="9f886-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="9f886-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの双方向の操作を呼び出す場合、このサービスには、従来の命令型のコード ベースの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを使用することも、ワークフロー サービスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9f886-104">When invoking a two-way operation in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, the service can be either a traditional imperative code-based [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="9f886-105">要求/応答の相関関係を使用するには、<xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f886-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="9f886-106">双方向の操作を呼び出す場合と実装する場合では、相関関係の初期化に同様の手順が使用されます。これらの手順については、このセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="9f886-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="9f886-107">Receive/SendReply による双方向の操作での相関関係の使用</span><span class="sxs-lookup"><span data-stu-id="9f886-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="9f886-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアは、ワークフロー サービスに双方向の操作を実装するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9f886-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="9f886-109">ランタイムは、要求/応答の相関関係を使用して、応答が正しい呼び出し元にディスパッチされるようにします。</span><span class="sxs-lookup"><span data-stu-id="9f886-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="9f886-110">ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合、つまり、ワークフロー サービスの場合は、既定の相関関係の初期化で十分です。</span><span class="sxs-lookup"><span data-stu-id="9f886-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="9f886-111">このシナリオでは、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアは、ワークフローで使用して、特定の相関関係の構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9f886-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="9f886-112">要求/応答の相関関係の明示的な初期化</span><span class="sxs-lookup"><span data-stu-id="9f886-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="9f886-113">他の双方向の操作が並列実行される場合、相関関係を明示的に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f886-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="9f886-114">指定することによってこれ行う、<xref:System.ServiceModel.Activities.CorrelationHandle>と<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>、または配置することによって、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>の内側、<xref:System.ServiceModel.Activities.CorrelationScope>です。</span><span class="sxs-lookup"><span data-stu-id="9f886-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="9f886-115">この例では要求-応答の相関関係が構成されている、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペア。</span><span class="sxs-lookup"><span data-stu-id="9f886-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="9f886-116">相関関係を明示的に構成する代わりに、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9f886-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="9f886-117"><xref:System.ServiceModel.Activities.CorrelationScope> は、内包しているメッセージング アクティビティに暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> を提供します。</span><span class="sxs-lookup"><span data-stu-id="9f886-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="9f886-118">この例では、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアに含まれている、<xref:System.ServiceModel.Activities.CorrelationScope>です。</span><span class="sxs-lookup"><span data-stu-id="9f886-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="9f886-119">明示的な相関関係の構成は不要です。</span><span class="sxs-lookup"><span data-stu-id="9f886-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="9f886-120">追加の相関関係が必要な場合は、目的の種類の <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> を使用する各メッセージング アクティビティの `CorrelationInitializer` プロパティを使用して、追加の相関関係を構成します。</span><span class="sxs-lookup"><span data-stu-id="9f886-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="9f886-121">Send/ReceiveReply による双方向の操作での相関関係の使用</span><span class="sxs-lookup"><span data-stu-id="9f886-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="9f886-122">中に、<xref:System.ServiceModel.Activities.Receive>アクティビティは、によってホストされるワークフロー サービスでのみ使用できます<xref:System.ServiceModel.Activities.WorkflowServiceHost>、<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペアは、Web サービスに対してメソッドを呼び出す必要のあるすべてのワークフローで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f886-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="9f886-123">ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされる場合は、前のセクションで説明した既定の相関関係が適用されますが、そうでない場合は、目的の <xref:System.ServiceModel.Activities.CorrelationInitializer> と <xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に使用するか、<xref:System.ServiceModel.Activities.CorrelationScope> による暗黙の処理管理を使用して、相関関係を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f886-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="9f886-124">使用する場合**サービス参照の追加**アクティビティを生成する双方向の操作で、サービスでラップする、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペア要求/応答の相関関係で内部的にアクティビティを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="9f886-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
