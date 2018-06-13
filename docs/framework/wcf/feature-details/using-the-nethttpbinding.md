---
title: NetHttpBinding の使用
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: a753cca008c7eb9b500afa7f3f3b55b5410522a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498870"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="4c893-102">NetHttpBinding の使用</span><span class="sxs-lookup"><span data-stu-id="4c893-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="4c893-103"><xref:System.ServiceModel.NetHttpBinding> は、HTTP や WebSocket のサービスを使用するために設計されたバインドで、既定ではバイナリ エンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c893-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="4c893-104"><xref:System.ServiceModel.NetHttpBinding> は、要求-応答コントラクトと二重のコントラクトのどちらで使用されているかを検出し、一致するように動作を変更します。要求-応答コントラクトには HTTP、二重のコントラクトには Websocket を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c893-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="4c893-105">使用してこの動作をオーバーライドすることができます、 <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage`設定。</span><span class="sxs-lookup"><span data-stu-id="4c893-105">This behavior can be overridden using the <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` setting:</span></span>  
  
1.  <span data-ttu-id="4c893-106">Always - 要求-応答コントラクトでも Websocket が使用されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4c893-106">Always - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2.  <span data-ttu-id="4c893-107">Never - Websocket が使用されないようにします。</span><span class="sxs-lookup"><span data-stu-id="4c893-107">Never - This prevents WebSockets from being used.</span></span> <span data-ttu-id="4c893-108">この設定で二重のコントラクトを使用しようとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="4c893-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3.  <span data-ttu-id="4c893-109">WhenDuplex - これが既定値で、既に説明したように動作します。</span><span class="sxs-lookup"><span data-stu-id="4c893-109">WhenDuplex - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="4c893-110"><xref:System.ServiceModel.NetHttpBinding> は、HTTP モードと WebSocket モードの両方で信頼できるセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="4c893-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="4c893-111">WebSocket モードでは、セッションがトランスポートによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="4c893-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4c893-112"><xref:System.ServiceModel.NetHttpBinding> を使用していて、バインドの TransferMode が TransferMode.Streamed に設定されている場合、大きいストリームによってデッドロックが発生する可能性があり、呼び出しがタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="4c893-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="4c893-113">この問題を回避するには、小さいメッセージを送信するか、TransferMode.Buffered を使用してください。</span><span class="sxs-lookup"><span data-stu-id="4c893-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="4c893-114">NetHttpBinding を使用するサービスの構成</span><span class="sxs-lookup"><span data-stu-id="4c893-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="4c893-115"><xref:System.ServiceModel.NetHttpBinding> は、他のバインドと同様に構成できます。</span><span class="sxs-lookup"><span data-stu-id="4c893-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="4c893-116">次の構成スニペットは、<xref:System.ServiceModel.NetHttpBinding> を使用して WCF サービスを構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c893-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 <span data-ttu-id="4c893-117">次のコード スニペットは、コードで <xref:System.ServiceModel.NetHttpBinding> を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c893-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c893-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c893-118">See Also</span></span>  
 [<span data-ttu-id="4c893-119">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="4c893-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="4c893-120">バインディング</span><span class="sxs-lookup"><span data-stu-id="4c893-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="4c893-121">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="4c893-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="4c893-122">双方向サービス</span><span class="sxs-lookup"><span data-stu-id="4c893-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
