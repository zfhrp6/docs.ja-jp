---
title: "WCF サービスからの REST スタイル サービスの呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b056e2c4dad46429462b377994919b46109cb9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="8cfa5-102">WCF サービスからの REST スタイル サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="8cfa5-102">Calling a REST-style service from a WCF service</span></span>
<span data-ttu-id="8cfa5-103">標準の (SOAP ベース) WCF サービスから REST スタイルのサービスを呼び出すとき、受信要求に関する情報を含んでいるサービス メソッドの操作コンテキストは、送信要求が使用するコンテキストをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="8cfa5-104">これにより、HTTP GET 要求は HTTP POST 要求に変更されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="8cfa5-105">WCF サービスが正しいコンテキストを使用して REST スタイルのサービスを呼び出すには、新しい <xref:System.ServiceModel.OperationContextScope> を作成し、操作コンテキスト スコープ内から REST スタイルのサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="8cfa5-106">このトピックでは、この手法を説明する簡単なサンプルを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>  
  
## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="8cfa5-107">REST スタイルのサービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="8cfa5-107">Define the REST-style service contract</span></span>  
 <span data-ttu-id="8cfa5-108">簡単な REST スタイルのサービス コントラクトを定義する:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-108">Define a simple  REST-style service contract:</span></span>  
  
```csharp
[ServiceContract]
public interface IRestInterface  
{  
    [OperationContract, WebGet]
    int Add(int x, int y);
    
    [OperationContract, WebGet]
    string Echo(string input);
}
```
  
## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="8cfa5-109">REST スタイルのサービス コントラクトを実装する</span><span class="sxs-lookup"><span data-stu-id="8cfa5-109">Implement the REST-style service contract</span></span>  
 <span data-ttu-id="8cfa5-110">REST スタイルのサービス コントラクトを実装する:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-110">Implement the REST-style service contract:</span></span>  
  
```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }
    
    public string Echo(string input)
    {
        return input;
    }
}
```
  
## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="8cfa5-111">WCF サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="8cfa5-111">Define the WCF service contract</span></span>  
 <span data-ttu-id="8cfa5-112">REST スタイルのサービスの呼び出しに使用する WCF サービス コントラクトを定義する:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>  
  
```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);
    
    [OperationContract]
    string CallEcho(string input);
}
```  
  
## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="8cfa5-113">WCF サービス コントラクトを実装する</span><span class="sxs-lookup"><span data-stu-id="8cfa5-113">Implement the WCF service contract</span></span>  
 <span data-ttu-id="8cfa5-114">WCF サービス コントラクトを実装する:</span><span class="sxs-lookup"><span data-stu-id="8cfa5-114">Implement the WCF service contract:</span></span>  
  
```csharp
public class NormalService : INormalInterface  
{  
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
    public int CallAdd(int x, int y)  
    {  
        return client.Add(x, y);  
    }  
    
    public string CallEcho(string input)  
    {  
        return client.Echo(input);  
    }  
}  
```  
  
## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="8cfa5-115">REST スタイルのサービスのクライアント プロキシを作成する</span><span class="sxs-lookup"><span data-stu-id="8cfa5-115">Create the client proxy for the REST-style service</span></span>  
 <span data-ttu-id="8cfa5-116">使用して<!--zz<xref:System.ServiceModel.ClientBase%60>-->`System.ServiceModel.ClientBase`クライアント プロキシを実装します。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-116">Using <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` implement the client proxy.</span></span> <span data-ttu-id="8cfa5-117">呼び出される各メソッドで、新しい <xref:System.ServiceModel.OperationContextScope> が作成され、操作の呼び出しに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>  
  
```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```  
  
## <a name="host-and-call-the-services"></a><span data-ttu-id="8cfa5-118">サービスをホストし、呼び出す</span><span class="sxs-lookup"><span data-stu-id="8cfa5-118">Host and call the services</span></span>  
 <span data-ttu-id="8cfa5-119">コンソール アプリケーションの両方のサービスをホストし、必要なエンドポイントと動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="8cfa5-120">次に、通常の WCF サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-120">And then call the regular WCF service:</span></span>  
  
```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```  
  
## <a name="complete-code-listing"></a><span data-ttu-id="8cfa5-121">完全なコード リスト</span><span class="sxs-lookup"><span data-stu-id="8cfa5-121">Complete code listing</span></span>  
 <span data-ttu-id="8cfa5-122">このトピックで実装されるサンプルの完全なコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8cfa5-122">The following is a complete listing of the sample implemented in this topic:</span></span>  
  
```csharp
public class CallingRESTSample  
{  
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";  
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";  

    [ServiceContract]  
    public interface IRestInterface  
    {  
        [OperationContract, WebGet]  
        int Add(int x, int y);  
        [OperationContract, WebGet]  
        string Echo(string input);  
    }  

    [ServiceContract]  
    public interface INormalInterface  
    {  
        [OperationContract]  
        int CallAdd(int x, int y);  
        [OperationContract]  
        string CallEcho(string input);  
    }  

    public class RestService : IRestInterface  
    {  
        public int Add(int x, int y)  
        {  
            return x + y;  
        }  

        public string Echo(string input)  
        {  
            return input;  
        }  
    }  

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface  
    {  
        public MyRestClient(string address)  
            : base(new WebHttpBinding(), new EndpointAddress(address))  
        {  
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());  
        }  

        public int Add(int x, int y)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Add(x, y);  
            }  
        }  

        public string Echo(string input)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Echo(input);  
            }  
        }  
    }  

    public class NormalService : INormalInterface  
    {  
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
        public int CallAdd(int x, int y)  
        {  
            return client.Add(x, y);  
        }  

        public string CallEcho(string input)  
        {  
            return client.Echo(input);  
        }  
    }
    
    public static void Main()  
    {  
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));  
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
        restHost.Open();  

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));  
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");  
        normalHost.Open();  

        Console.WriteLine("Hosts opened");  

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));  
        INormalInterface proxy = factory.CreateChannel();  

        Console.WriteLine(proxy.CallAdd(123, 456));  
        Console.WriteLine(proxy.CallEcho("Hello world"));  
    }  
}
```
  
## <a name="see-also"></a><span data-ttu-id="8cfa5-123">参照</span><span class="sxs-lookup"><span data-stu-id="8cfa5-123">See Also</span></span>  
 [<span data-ttu-id="8cfa5-124">方法 : 基本的な WCF Web HTTP サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="8cfa5-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 [<span data-ttu-id="8cfa5-125">WCF Web HTTP プログラミング オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="8cfa5-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
