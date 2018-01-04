---
title: "方法 : クライアントのメッセージを検査または変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06f4feaa5b0b44a26e3d31b65dc465b67544482f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="549f7-102">方法 : クライアントのメッセージを検査または変更する</span><span class="sxs-lookup"><span data-stu-id="549f7-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="549f7-103">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を実装し、それをクライアントのランタイムに追加することで、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> クライアントの送受信メッセージを検査または変更できます。</span><span class="sxs-lookup"><span data-stu-id="549f7-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="549f7-104">詳細については、次を参照してください。[を拡張するクライアント](../../../../docs/framework/wcf/extending/extending-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="549f7-104">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="549f7-105">サービスの同等の機能は、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="549f7-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="549f7-106">完全なコード例については、[メッセージ インスペクタ](../../../../docs/framework/wcf/samples/message-inspectors.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="549f7-106">For a complete code example see the [Message Inspectors](../../../../docs/framework/wcf/samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="549f7-107">メッセージを検査または変更するには</span><span class="sxs-lookup"><span data-stu-id="549f7-107">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="549f7-108"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="549f7-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="549f7-109">クライアント メッセージ インスペクターを挿入するスコープに応じて、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> を実装します。</span><span class="sxs-lookup"><span data-stu-id="549f7-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="549f7-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>使用すると、エンドポイント レベルでの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="549f7-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="549f7-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>コントラクト レベルの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="549f7-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3.  <span data-ttu-id="549f7-112"><xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> メソッドまたは <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> メソッドを呼び出す前に、動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="549f7-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="549f7-113">詳細については、「[を構成して、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="549f7-113">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="549f7-114">例</span><span class="sxs-lookup"><span data-stu-id="549f7-114">Example</span></span>  
 <span data-ttu-id="549f7-115">下のコード例では、次の項目を順番に示しています。</span><span class="sxs-lookup"><span data-stu-id="549f7-115">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="549f7-116">クライアント インスペクター実装</span><span class="sxs-lookup"><span data-stu-id="549f7-116">A client inspector implementation.</span></span>  
  
-   <span data-ttu-id="549f7-117">インスペクターを挿入するエンドポイント動作</span><span class="sxs-lookup"><span data-stu-id="549f7-117">An endpoint behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="549f7-118">構成ファイルで動作を追加できるようにする <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 派生クラス。</span><span class="sxs-lookup"><span data-stu-id="549f7-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
-   <span data-ttu-id="549f7-119">クライアント メッセージ インスペクターをクライアント ランタイムに挿入するエンドポイント動作を追加する構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="549f7-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client   
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they   
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element   
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"   
                      binding="wsHttpBinding"  
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="549f7-120">参照</span><span class="sxs-lookup"><span data-stu-id="549f7-120">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="549f7-121">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="549f7-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
