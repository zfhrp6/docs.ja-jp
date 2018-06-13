---
title: コンテキスト交換の相関関係
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: da5ab2c89e4e2011c38f5fca99aeb5c2c73801a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492324"
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="512a2-102">コンテキスト交換の相関関係</span><span class="sxs-lookup"><span data-stu-id="512a2-102">Context Exchange Correlation</span></span>
<span data-ttu-id="512a2-103">コンテキスト相関関係はで説明されているコンテキスト交換機構に基づいて、 [.NET コンテキスト交換プロトコルの仕様](http://go.microsoft.com/fwlink/?LinkId=166059)です。</span><span class="sxs-lookup"><span data-stu-id="512a2-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="512a2-104">コンテキスト相関関係では、既知のコンテキスト ヘッダーまたはクッキーを使用して、メッセージを正しいインスタンスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="512a2-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="512a2-105">コンテキスト相関関係を使用するには、<xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding>、<xref:System.ServiceModel.NetTcpContextBinding> などのコンテキスト ベースのバインディングが、<xref:System.ServiceModel.Activities.WorkflowServiceHost> に提供されるエンドポイントで使用される必要があります。</span><span class="sxs-lookup"><span data-stu-id="512a2-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="512a2-106">このトピックでは、メッセージング アクティビティを指定したコンテキスト相関関係をワークフロー サービス内で使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="512a2-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="512a2-107">コンテキスト相関関係の使用</span><span class="sxs-lookup"><span data-stu-id="512a2-107">Using Context Correlation</span></span>  
 <span data-ttu-id="512a2-108">クライアントがワークフロー サービスに繰り返し呼び出しを行う必要があり、そのサービスがコンテキスト バインディングの 1 つを使用してホストされている場合に、コンテキスト相関関係が使用されます。</span><span class="sxs-lookup"><span data-stu-id="512a2-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="512a2-109">この種類の相関関係はによって初期化、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ワークフロー サービス内のペア。</span><span class="sxs-lookup"><span data-stu-id="512a2-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="512a2-110">コンテキストは、応答と共にクライアントに送り返されます。その後、クライアントによって、サービスへの以降の呼び出しにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="512a2-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="512a2-111">ワークフロー サービス内でのコンテキスト相関関係の構成</span><span class="sxs-lookup"><span data-stu-id="512a2-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="512a2-112">コンテキスト相関関係は、最初の受信メッセージに応答する <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> アクティビティと関連付けられている <xref:System.ServiceModel.Activities.SendReply> を使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="512a2-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="512a2-113">次の例では、コンテキスト相関関係を初期化するように <xref:System.ServiceModel.Activities.SendReply> が構成されています。</span><span class="sxs-lookup"><span data-stu-id="512a2-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  <span data-ttu-id="512a2-114">この例では、実際にはコンテキストの関連付けおよび要求/応答の相関関係の 2 種類の相関関係が使用されています。</span><span class="sxs-lookup"><span data-stu-id="512a2-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="512a2-115">コンテキストの相関関係は、クライアントからの呼び出しが適切なインスタンスにルーティングされるように使用されます。</span><span class="sxs-lookup"><span data-stu-id="512a2-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="512a2-116">要求/応答の相関関係は、これらのアクティビティによってモデル化される双方向の操作を実装するために、<xref:System.ServiceModel.Activities.Receive> アクティビティおよび <xref:System.ServiceModel.Activities.SendReply> アクティビティで使用されます。</span><span class="sxs-lookup"><span data-stu-id="512a2-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="512a2-117">この例では、コンテキスト相関関係のみが明示的に構成、および<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアは、暗黙の型によって提供される既定の要求-応答の相関関係を使用して<xref:System.ServiceModel.Activities.CorrelationHandle>管理<xref:System.ServiceModel.Activities.WorkflowServiceHost>です。</span><span class="sxs-lookup"><span data-stu-id="512a2-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="512a2-118">使用する場合、 **ReceiveAndSendReply**ワークフロー デザイナーは、要求-応答の相関関係での活動テンプレートを明示的に構成します。</span><span class="sxs-lookup"><span data-stu-id="512a2-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> <span data-ttu-id="512a2-119">要求-応答の相関関係と暗黙の関連付けハンドル管理の詳細については、次を参照してください。[要求/応答](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)と[相関関係の概要](../../../../docs/framework/wcf/feature-details/correlation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="512a2-119">For more information about request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> <span data-ttu-id="512a2-120">詳細については、 **ReceiveAndSendReply**アクティビティ テンプレートを参照してください[ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer)です。</span><span class="sxs-lookup"><span data-stu-id="512a2-120">For more information about the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="512a2-121">ワークフロー サービス内の以降の <xref:System.ServiceModel.Activities.Receive> アクティビティは、前の例の <xref:System.ServiceModel.Activities.CorrelationHandle> で初期化された <xref:System.ServiceModel.Activities.SendReply> を参照できます。</span><span class="sxs-lookup"><span data-stu-id="512a2-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="512a2-122">エンドポイントは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> で、<xref:System.ServiceModel.BasicHttpContextBinding> などのコンテキスト ベースのバインディングを使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="512a2-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="512a2-123">ワークフロー クライアント内でのコンテキスト相関関係の構成</span><span class="sxs-lookup"><span data-stu-id="512a2-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="512a2-124">クライアントが別のワークフローである場合は、コンテキスト相関関係をクライアントでも構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="512a2-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="512a2-125">クライアント ワークフローで、<xref:System.ServiceModel.Activities.ReceiveReply>の<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>でワークフロー サービスへの最初の呼び出しは、ペアを構成する必要があります、<xref:System.ServiceModel.Activities.ContextCorrelationInitializer>です。</span><span class="sxs-lookup"><span data-stu-id="512a2-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 <span data-ttu-id="512a2-126">相関関係が初期化されると、以降の <xref:System.ServiceModel.Activities.Send> アクティビティでは、<xref:System.ServiceModel.Activities.CorrelationHandle> を使用して、同じサービス インスタンスでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="512a2-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="512a2-127">これらの例では、コンテキスト相関関係が明示的に構成されています。</span><span class="sxs-lookup"><span data-stu-id="512a2-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="512a2-128">クライアント ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> でもホストされていない場合は、アクティビティが <xref:System.ServiceModel.Activities.CorrelationScope> アクティビティ内に含まれていない限り、相関関係を明示的に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="512a2-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> <span data-ttu-id="512a2-129">コンテキスト相関関係の詳細については、次を参照してください。、 [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="512a2-129">For more information about context correlation, see the [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="512a2-130">ワークフロー サービスへの呼び出しを行うクライアントがワークフローではない場合でも、ワークフロー サービスへの最初の呼び出しで返されたコンテキストを明示的に渡す限り、呼び出しを繰り返して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="512a2-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="512a2-131">サービス参照を [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ストアに追加することでプロキシが生成され、このコンテキストが既定で渡されます。</span><span class="sxs-lookup"><span data-stu-id="512a2-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
