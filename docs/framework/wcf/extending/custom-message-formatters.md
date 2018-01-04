---
title: "カスタム メッセージ フォーマッタ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea32656db90907ae523502fc1796466442ef4a4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-formatters"></a><span data-ttu-id="86367-102">カスタム メッセージ フォーマッタ</span><span class="sxs-lookup"><span data-stu-id="86367-102">Custom Message Formatters</span></span>
<span data-ttu-id="86367-103">メッセージの内容は、XML 形式で表されることが多く、この形式は通常、アプリケーションにとって処理しやすい形式ではありません。</span><span class="sxs-lookup"><span data-stu-id="86367-103">The content in a message is often in the form of XML, which is usually not a convenient format for an application.</span></span> <span data-ttu-id="86367-104">アプリケーションでは、オブジェクトのプロパティを取得および設定することによってオブジェクトを操作します。</span><span class="sxs-lookup"><span data-stu-id="86367-104">Applications manipulate objects, getting and setting their properties.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="86367-105">使用して、*データ コントラクト*に変換する、<xref:System.ServiceModel.Channels.Message>オブジェクトに、オブジェクトをアプリケーションで簡単に処理します。</span><span class="sxs-lookup"><span data-stu-id="86367-105"> uses the *Data Contract* to convert a <xref:System.ServiceModel.Channels.Message> object into an object easily handled by an application.</span></span> <span data-ttu-id="86367-106">このプロセスは、シリアル化および逆シリアル化と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="86367-106">These processes are called serialization and deserialization.</span></span> <span data-ttu-id="86367-107">これと同じ用語が、トランスポート層によって行われるメッセージ ワイヤ形式へのシリアル化とその形式からの逆シリアル化を説明するときに使用されますが、これは関連のないプロセスです。</span><span class="sxs-lookup"><span data-stu-id="86367-107">Note that these same terms are used to describe the serialization and deserialization done by the transport layer to and from the message wire format, which is an unrelated process.</span></span>  
  
 <span data-ttu-id="86367-108">データ コントラクトによって実現できないメッセージとオブジェクト間の特殊な変換を実装する必要がある場合、カスタム メッセージ フォーマッタを使用できます。</span><span class="sxs-lookup"><span data-stu-id="86367-108">You can use a custom message formatter if you need to implement a specialized conversion between messages and objects that you cannot accomplish by means of a Data Contract.</span></span> <span data-ttu-id="86367-109">これを使用するには、クライアントまたはサービス上で特定のコントラクト操作の実行動作を変更または拡張します。</span><span class="sxs-lookup"><span data-stu-id="86367-109">Do this by modifying or extending the execution behavior of a specific contract operation on a client or a service.</span></span>  
  
## <a name="custom-message-formatters-on-the-client"></a><span data-ttu-id="86367-110">クライアントのカスタム メッセージ フォーマッタ</span><span class="sxs-lookup"><span data-stu-id="86367-110">Custom Message Formatters on the Client</span></span>  
 <span data-ttu-id="86367-111"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> インターフェイスは、メッセージからオブジェクトへの変換およびオブジェクトからクライアント アプリケーション用のメッセージへの変換を制御するためのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="86367-111">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface defines methods that are used to control the conversion of messages into objects and objects into messages for client applications.</span></span>  
  
 <span data-ttu-id="86367-112">このインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86367-112">You must implement this interface.</span></span> <span data-ttu-id="86367-113">まず、メッセージを逆シリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="86367-113">First override the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> method to deserialize a message.</span></span> <span data-ttu-id="86367-114">このメソッドは、受信メッセージを受信した後でそのメッセージがクライアント操作にディスパッチされる前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86367-114">This method is called after an incoming message is received, but before it is dispatched to the client operation.</span></span>  
  
 <span data-ttu-id="86367-115">次に、オブジェクトをシリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="86367-115">Next, override the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> method to serialize an object.</span></span> <span data-ttu-id="86367-116">このメソッドは、送信メッセージを送信する前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86367-116">This method is called prior to sending an outgoing message.</span></span>  
  
 <span data-ttu-id="86367-117">カスタム フォーマッタをサービス アプリケーションに挿入するには、操作の動作を使用して、<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> オブジェクトを <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="86367-117">To insert the custom formatter into the service application, assign the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> object to the <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> property using an operation behavior.</span></span> <span data-ttu-id="86367-118">動作方法については、次を参照してください。[を構成すると、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="86367-118">For information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="custom-message-formatters-on-the-service"></a><span data-ttu-id="86367-119">サービスのカスタム メッセージ フォーマッタ</span><span class="sxs-lookup"><span data-stu-id="86367-119">Custom Message Formatters on the Service</span></span>  
 <span data-ttu-id="86367-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> インターフェイスは、<xref:System.ServiceModel.Channels.Message> オブジェクトを操作用のパラメーターに変換し、これらのパラメーターをサービス アプリケーション用の <xref:System.ServiceModel.Channels.Message> オブジェクトに変換するためのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="86367-120">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface defines methods that convert a <xref:System.ServiceModel.Channels.Message> object into parameters for an operation and from parameters into a <xref:System.ServiceModel.Channels.Message> object in a service application.</span></span>  
  
 <span data-ttu-id="86367-121">このインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86367-121">You must implement this interface.</span></span> <span data-ttu-id="86367-122">まず、メッセージを逆シリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="86367-122">First override the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> method to deserialize a message.</span></span> <span data-ttu-id="86367-123">このメソッドは、受信メッセージを受信した後でそのメッセージがクライアント操作にディスパッチされる前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86367-123">This method is called after an incoming message is received, but before it is dispatched to the client operation.</span></span>  
  
 <span data-ttu-id="86367-124">次に、オブジェクトをシリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="86367-124">Next, override the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> method to serialize an object.</span></span> <span data-ttu-id="86367-125">このメソッドは、送信メッセージを送信する前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86367-125">This method is called prior to sending an outgoing message.</span></span>  
  
 <span data-ttu-id="86367-126">カスタム フォーマッタをサービス アプリケーションに挿入するには、操作の動作を使用して、<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> オブジェクトを <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="86367-126">To insert the custom formatter into the service application, assign the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> object to the <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> property using an operation behavior.</span></span> <span data-ttu-id="86367-127">動作方法については、次を参照してください。[を構成すると、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="86367-127">For information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86367-128">参照</span><span class="sxs-lookup"><span data-stu-id="86367-128">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [<span data-ttu-id="86367-129">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="86367-129">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
