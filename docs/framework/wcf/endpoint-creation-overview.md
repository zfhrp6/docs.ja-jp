---
title: "エンドポイントの作成の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa20edd8fa43fb1e6a28f7b1ec18f83fedd96bca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="2784c-102">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="2784c-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="2784c-103">すべての通信、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]サービスが使用して行われる、*エンドポイント*サービス。</span><span class="sxs-lookup"><span data-stu-id="2784c-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="2784c-104">エンドポイントは、クライアントが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスによって提供される機能にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2784c-104">Endpoints provide the clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span> <span data-ttu-id="2784c-105">ここでは、エンドポイントの構造を説明し、構成やコード内にエンドポイントを定義する方法を概説します。</span><span class="sxs-lookup"><span data-stu-id="2784c-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="2784c-106">エンドポイントの構造</span><span class="sxs-lookup"><span data-stu-id="2784c-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="2784c-107">各エンドポイントは、そのエンドポイントが存在する場所を示すアドレス、クライアントがエンドポイントと通信するための方法を指定するバインディング、および利用可能なメソッドを特定するコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2784c-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="2784c-108">**アドレス**です。</span><span class="sxs-lookup"><span data-stu-id="2784c-108">**Address**.</span></span> <span data-ttu-id="2784c-109">アドレスは、エンドポイントを一意に識別し、潜在的ユーザーにそのサービスの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="2784c-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="2784c-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] オブジェクト モデルでは、<xref:System.ServiceModel.EndpointAddress> アドレスで表されます。このアドレスは、URI (Uniform Resource Identifier) とアドレス プロパティ (ID、Web サービス記述言語 (WSDL) 要素、およびオプション ヘッダーのコレクションを含む) を格納します。</span><span class="sxs-lookup"><span data-stu-id="2784c-110">It is represented in the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="2784c-111">オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2784c-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="2784c-112">[エンドポイント アドレスを指定する](../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。</span><span class="sxs-lookup"><span data-stu-id="2784c-112"> [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="2784c-113">**バインド**です。</span><span class="sxs-lookup"><span data-stu-id="2784c-113">**Binding**.</span></span> <span data-ttu-id="2784c-114">バインディングはエンドポイントとの通信方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="2784c-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="2784c-115">バインディングでは、使用するトランスポート プロトコル (TCP や HTTP)、メッセージのエンコーディング方法 (テキストやバイナリ)、必要なセキュリティ要件 (SSL (Secure Sockets Layer) や SOAP メッセージ セキュリティ) など、そのエンドポイントがどのように通信を行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2784c-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="2784c-116">[バインディングを使用してサービスとクライアントを構成する](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="2784c-116"> [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="2784c-117">**サービス コントラクト**です。</span><span class="sxs-lookup"><span data-stu-id="2784c-117">**Service contract**.</span></span> <span data-ttu-id="2784c-118">サービス コントラクトは、エンドポイントがクライアントに公開する機能を示します。</span><span class="sxs-lookup"><span data-stu-id="2784c-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="2784c-119">コントラクトは、クライアントが呼び出すことのできる操作、メッセージの形式、操作の呼び出しに必要な入力パラメーターやデータの型、クライアントに提供する処理または応答メッセージの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="2784c-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="2784c-120">基本的なメッセージ交換パターン (MEP) に対応する基本的なコントラクトの種類には、データグラム (一方向)、要求/応答、二重 (双方向) の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="2784c-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="2784c-121">サービス コントラクトは、データ コントラクトとメッセージ コントラクトを使用して、クライアントが特定のデータ型とメッセージ形式でアクセスするように要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="2784c-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="2784c-122">サービス コントラクトを定義する方法[サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="2784c-122"> how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="2784c-123">クライアントでは、二重 MEP でサービスからメッセージを受信するために、コールバック コントラクトというサービス定義のコントラクトを実装することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2784c-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="2784c-124">[双方向サービス](../../../docs/framework/wcf/feature-details/duplex-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="2784c-124"> [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="2784c-125">サービスのエンドポイントはコードを使用して強制的に指定するか、構成を介して宣言として指定できます。</span><span class="sxs-lookup"><span data-stu-id="2784c-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="2784c-126">エンドポイントが指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="2784c-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="2784c-127">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="2784c-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="2784c-128">一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。</span><span class="sxs-lookup"><span data-stu-id="2784c-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="2784c-129">バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="2784c-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2784c-130">偽装を行うサービス エンドポイントを追加する場合は、<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドまたは <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> メソッドのいずれかを使用して、コントラクトを新しい <xref:System.ServiceModel.Description.ServiceDescription> オブジェクトに適切に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="2784c-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="2784c-131">コードでのエンドポイントの定義</span><span class="sxs-lookup"><span data-stu-id="2784c-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="2784c-132">次の例は、コードにエンドポイントを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2784c-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="2784c-133">コントラクトを定義、`IEcho`を他のユーザーの名前とエコーで応答を受け付けるサービスの種類"こんにちは\<名前 >!"です。</span><span class="sxs-lookup"><span data-stu-id="2784c-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="2784c-134">`Echo` コントラクトで定義された型の `IEcho` サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2784c-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="2784c-135">サービスのエンドポイント アドレスとして http://localhost:8000/Echo を指定します。</span><span class="sxs-lookup"><span data-stu-id="2784c-135">Specify an endpoint address of http://localhost:8000/Echo for the service.</span></span>  
  
-   <span data-ttu-id="2784c-136">`Echo` バインディングを使用して <xref:System.ServiceModel.WSHttpBinding> サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="2784c-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  <span data-ttu-id="2784c-137">サービス ホストはベース アドレスを使用して作成されます。また、残りのアドレス (ベース アドレスの相対アドレス) はエンドポイントの一部として指定されます。</span><span class="sxs-lookup"><span data-stu-id="2784c-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="2784c-138">このようにアドレスを分割することで、ホストのサービスで複数のエンドポイントを簡単に定義できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2784c-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2784c-139"><xref:System.ServiceModel.Description.ServiceDescription> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> メソッドの後で、サービス アプリケーションの <xref:System.ServiceModel.ServiceHostBase> の各プロパティを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="2784c-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="2784c-140">このメソッドの後で変更すると、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> および `AddServiceEndpoint` の <xref:System.ServiceModel.ServiceHostBase> プロパティや <xref:System.ServiceModel.ServiceHost> メソッドなどの一部のメンバーは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="2784c-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="2784c-141">変更を許可するメンバーもありますが、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="2784c-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="2784c-142">同様に、クライアントで、<xref:System.ServiceModel.Description.ServiceEndpoint> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 呼び出しの後で、<xref:System.ServiceModel.ChannelFactory> 値を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="2784c-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="2784c-143">この呼び出しの後で変更すると、<xref:System.ServiceModel.ChannelFactory.Credentials%2A> プロパティは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="2784c-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="2784c-144">その他のクライアント記述値は、エラーを発生させずに変更できますが、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="2784c-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="2784c-145">サービスとクライアントのどちらの場合も、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> の呼び出しの前に記述を変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2784c-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="2784c-146">構成でのエンドポイントの定義</span><span class="sxs-lookup"><span data-stu-id="2784c-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="2784c-147">アプリケーションの作成では、各種決定事項をアプリケーションを展開する管理者に任せる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="2784c-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="2784c-148">たとえば、どのサービス アドレス (URI) を使用するかなどの情報は、前もって知るすべがありません。</span><span class="sxs-lookup"><span data-stu-id="2784c-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="2784c-149">アドレスをハードコーディングする代わりに、サービスの作成後に管理者が指定する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="2784c-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="2784c-150">構成を活用することで、この柔軟性が得られます。</span><span class="sxs-lookup"><span data-stu-id="2784c-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="2784c-151">詳細については、「[サービスを構成する](../../../docs/framework/wcf/configuring-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="2784c-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2784c-152">使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)で、 `/config:` *filename*`[,`*filename* `]`に切り替える構成ファイルをすばやく作成します。</span><span class="sxs-lookup"><span data-stu-id="2784c-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="2784c-153">既定のエンドポイントの使用</span><span class="sxs-lookup"><span data-stu-id="2784c-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="2784c-154">エンドポイントがコードまたは構成で指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="2784c-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="2784c-155">ベース アドレスはコードまたは構成で指定することができ、既定のエンドポイントは、<xref:System.ServiceModel.ICommunicationObject.Open> が <xref:System.ServiceModel.ServiceHost> で呼び出されるときに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2784c-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2784c-156">次の例は上記のセクションの例と同じです。ただし、エンドポイントを指定せず、既定のエンドポイントを追加する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="2784c-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 <span data-ttu-id="2784c-157">エンドポイントを明示的に指定しない場合、<xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> を呼び出す前に、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> を呼び出すことによって、既定のエンドポイントを引き続き追加できます。</span><span class="sxs-lookup"><span data-stu-id="2784c-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="2784c-158">既定のエンドポイントを参照してください[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="2784c-158"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2784c-159">参照</span><span class="sxs-lookup"><span data-stu-id="2784c-159">See Also</span></span>  
 [<span data-ttu-id="2784c-160">サービス コントラクトの実装</span><span class="sxs-lookup"><span data-stu-id="2784c-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
