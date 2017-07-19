---
title: "コンテキスト交換の相関関係 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# コンテキスト交換の相関関係
コンテキスト相関関係は、[.NET コンテキスト交換プロトコルの仕様](http://go.microsoft.com/fwlink/?LinkId=166059)で説明されているコンテキスト交換メカニズムに基づきます。コンテキスト相関関係では、既知のコンテキスト ヘッダーまたはクッキーを使用して、メッセージを正しいインスタンスに関連付けます。コンテキスト相関関係を使用するには、<xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding>、<xref:System.ServiceModel.NetTcpContextBinding> などのコンテキスト ベースのバインディングが、<xref:System.ServiceModel.Activities.WorkflowServiceHost> に提供されるエンドポイントで使用される必要があります。このトピックでは、メッセージング アクティビティを指定したコンテキスト相関関係をワークフロー サービス内で使用する方法について説明します。  
  
## コンテキスト相関関係の使用  
 クライアントがワークフロー サービスに繰り返し呼び出しを行う必要があり、そのサービスがコンテキスト バインディングの 1 つを使用してホストされている場合に、コンテキスト相関関係が使用されます。この種類の相関関係は、ワークフロー サービス内で <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> のペアによって初期化されます。コンテキストは、応答と共にクライアントに送り返されます。その後、クライアントによって、サービスへの以降の呼び出しにアタッチされます。  
  
### ワークフロー サービス内でのコンテキスト相関関係の構成  
 コンテキスト相関関係は、最初の受信メッセージに応答する <xref:System.ServiceModel.Activities.SendReply> アクティビティと関連付けられている <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> を使用して初期化されます。次の例では、コンテキスト相関関係を初期化するように <xref:System.ServiceModel.Activities.SendReply> が構成されています。  
  
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
>  この例では、実際にはコンテキストの関連付けおよび要求\/応答の相関関係の 2 種類の相関関係が使用されています。コンテキストの相関関係は、クライアントからの呼び出しが適切なインスタンスにルーティングされるように使用されます。要求\/応答の相関関係は、これらのアクティビティによってモデル化される双方向の操作を実装するために、<xref:System.ServiceModel.Activities.Receive> アクティビティおよび <xref:System.ServiceModel.Activities.SendReply> アクティビティで使用されます。この例では、コンテキストの相関関係のみが明示的に構成され、<xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> ペアは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> の暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> 管理で提供される、既定の要求\/応答の相関関係を使用しています。ワークフロー デザイナーで **ReceiveAndSendReply** アクティビティ テンプレートを使用する場合、要求\/応答の相関関係は明示的に構成されます。要求\/応答の相関関係および暗黙の関連付けハンドル管理[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[要求\/応答](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)」および「[相関関係の概要](../../../../docs/framework/wcf/feature-details/correlation-overview.md)」を参照してください。**ReceiveAndSendReply** アクティビティ テンプレート[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ReceiveAndSendReply](../Topic/ReceiveAndSendReply%20Template%20Designer.md)」を参照してください。  
  
 ワークフロー サービス内の以降の <xref:System.ServiceModel.Activities.Receive> アクティビティは、前の例の <xref:System.ServiceModel.Activities.SendReply> で初期化された <xref:System.ServiceModel.Activities.CorrelationHandle> を参照できます。  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 エンドポイントは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> で、<xref:System.ServiceModel.BasicHttpContextBinding> などのコンテキスト ベースのバインディングを使用するように構成されます。  
  
```xml  
<endpoint  
  contract=”IOrderContract”  
  binding = “basicHttpContextBinding”  
  address=”http://localhost:8080/OrderService” />  
```  
  
### ワークフロー クライアント内でのコンテキスト相関関係の構成  
 クライアントが別のワークフローである場合は、コンテキスト相関関係をクライアントでも構成する必要があります。クライアント ワークフローでは、ワークフロー サービスへの最初の呼び出しを行う <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> ペアの <xref:System.ServiceModel.Activities.ReceiveReply> が、<xref:System.ServiceModel.Activities.ContextCorrelationInitializer> で構成される必要があります。  
  
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
  
 相関関係が初期化されると、以降の <xref:System.ServiceModel.Activities.Send> アクティビティでは、<xref:System.ServiceModel.Activities.CorrelationHandle> を使用して、同じサービス インスタンスでメソッドを呼び出すことができます。  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 これらの例では、コンテキスト相関関係が明示的に構成されています。クライアント ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> でもホストされていない場合は、アクティビティが <xref:System.ServiceModel.Activities.CorrelationScope> アクティビティ内に含まれていない限り、相関関係を明示的に構成する必要があります。コンテキスト相関関係[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[NetContextExchangeCorrelation](http://msdn.microsoft.com/ja-jp/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)」を参照してください。  
  
 ワークフロー サービスへの呼び出しを行うクライアントがワークフローではない場合でも、ワークフロー サービスへの最初の呼び出しで返されたコンテキストを明示的に渡す限り、呼び出しを繰り返して行うことができます。サービス参照を [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ストアに追加することでプロキシが生成され、このコンテキストが既定で渡されます。