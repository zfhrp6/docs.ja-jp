---
title: "POX アプリケーションとの相互運用性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6dbdd72dce196ea58550cff956a7b0e6fe0b1a73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="2b511-102">POX アプリケーションとの相互運用性</span><span class="sxs-lookup"><span data-stu-id="2b511-102">Interoperability with POX Applications</span></span>
<span data-ttu-id="2b511-103">"Plain Old XML"(POX) アプリケーションは、SOAP エンベロープで囲まれていない XML アプリケーション データのみを含んだ生の HTTP メッセージを交換して通信します。</span><span class="sxs-lookup"><span data-stu-id="2b511-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2b511-104"> では、POX メッセージを使用するサービスとクライアントの両方を提供できます。</span><span class="sxs-lookup"><span data-stu-id="2b511-104"> can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="2b511-105">サービスでは、POX メッセージを送受信する Web ブラウザーやスクリプト言語などのクライアントに対してエンドポイントを公開するサービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="2b511-105">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="2b511-106">クライアントでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] プログラミング モデルを使用して、POX ベースのサービスと通信するクライアントを実装できます。</span><span class="sxs-lookup"><span data-stu-id="2b511-106">On the client, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b511-107">このドキュメントはもともと [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 用に書かれたものです。</span><span class="sxs-lookup"><span data-stu-id="2b511-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]<span data-ttu-id="2b511-108"> 3.5 には POX アプリケーション用のサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="2b511-108"> 3.5 has built-in support for working with POX applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2b511-109">参照してください[WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="2b511-109"> see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span></span>  
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="2b511-110">WCF による POX プログラミング</span><span class="sxs-lookup"><span data-stu-id="2b511-110">POX Programming with WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b511-111">POX メッセージを使用して HTTP 経由で通信するサービスを[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b511-111"> services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="2b511-112">このカスタム バインドには、次の 2 つの要素があります。</span><span class="sxs-lookup"><span data-stu-id="2b511-112">This custom binding contains two elements:</span></span>  
  
-   <span data-ttu-id="2b511-113">[ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)と</span><span class="sxs-lookup"><span data-stu-id="2b511-113">The [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) and</span></span>  
  
-   <span data-ttu-id="2b511-114">[ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b511-114">The [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
 <span data-ttu-id="2b511-115">標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テキスト メッセージ エンコーダーで <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 値を使用するように特別に構成することにより、SOAP エンベロープにラップされずに到着する XML メッセージ ペイロードを処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2b511-115">The standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>  
  
 <span data-ttu-id="2b511-116">POX メッセージを使用して HTTP を介して通信する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントでも、次の強制コードに示すように、同様のバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b511-116">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 <span data-ttu-id="2b511-117">POX クライアントでは、メッセージの送信先となる URI を明示的に指定する必要があるため、クライアントの <xref:System.ServiceModel.Channels.HttpTransportBindingElement> プロパティを <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> に設定することで、通常、`true` を手動アドレス指定モードに構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b511-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="2b511-118">これにより、アプリケーション コードによってメッセージのアドレスが明示的に指定されることになり、アプリケーションで異なる HTTP URI にメッセージを送信するたびに、新しい <xref:System.ServiceModel.ChannelFactory> を作成する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="2b511-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>  
  
 <span data-ttu-id="2b511-119">POX メッセージでは重要なプロトコル情報の搬送に SOAP ヘッダーを使用しないため、POX クライアントおよびサービスでは、メッセージの送受信に使用される、基になる HTTP 要求の情報を操作する必要が生じる場合がよく起こります。</span><span class="sxs-lookup"><span data-stu-id="2b511-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="2b511-120">HTTP ヘッダーやステータス コードなど、HTTP 固有のプロトコル情報は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] プログラミング モデルでは次の 2 つのクラスを通じて表現されます。</span><span class="sxs-lookup"><span data-stu-id="2b511-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model through two classes:</span></span>  
  
-   <span data-ttu-id="2b511-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty> には、HTTP メソッドと要求ヘッダーなど、HTTP 要求についての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b511-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>  
  
-   <span data-ttu-id="2b511-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty> には、HTTP ステータス コード、ステータスの説明、および任意の HTTP 応答ヘッダーなど、HTTP 応答についての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b511-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>  
  
 <span data-ttu-id="2b511-123">http://localhost:8100/customers にアドレス指定される HTTP GET 要求メッセージの作成方法を、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="2b511-123">The following code example shows how to create an HTTP GET request message that is addressed to http://localhost:8100/customers.</span></span>  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 <span data-ttu-id="2b511-124">初めに、<xref:System.ServiceModel.Channels.Message> を呼び出すことで、空の <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> 要求を作成します。</span><span class="sxs-lookup"><span data-stu-id="2b511-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="2b511-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> パラメーターを使用して SOAP エンベロープが不要であることを示し、<xref:System.String.Empty> パラメーターをアクションとして渡します。</span><span class="sxs-lookup"><span data-stu-id="2b511-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="2b511-126">次に、<xref:System.ServiceModel.Channels.MessageHeaders.To%2A> を目的の URI に設定することで、要求メッセージをアドレス指定します。</span><span class="sxs-lookup"><span data-stu-id="2b511-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="2b511-127">さらに、<xref:System.ServiceModel.Channels.HttpRequestMessageProperty> を作成し、<xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> を HTTP 動詞の GET メソッドに設定し、また <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> を `true` に設定して、送信 HTTP 要求メッセージの本文でデータが送信されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2b511-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="2b511-128">最後に、要求プロパティを要求メッセージの <xref:System.ServiceModel.Channels.Message.Properties%2A> コレクションに追加して、HTTP トランスポートによる要求の送信方法に影響を与えることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="2b511-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="2b511-129">これで <xref:System.ServiceModel.Channels.IRequestChannel> の適切なインスタンスを使用してメッセージを送信する用意が整いました。</span><span class="sxs-lookup"><span data-stu-id="2b511-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>  
  
 <span data-ttu-id="2b511-130">サービスにおいても、受信メッセージから <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> を抽出して応答を構築する際に同様のテクニックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b511-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
