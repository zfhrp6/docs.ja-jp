---
title: "カスタム バインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a3da437f742c46a2229aa00db732b5437ec15e3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="custom-bindings"></a><span data-ttu-id="ed0f4-102">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="ed0f4-102">Custom Bindings</span></span>
<span data-ttu-id="ed0f4-103">システムが提供するバインディングの中にサービスの要件を満たすものがない場合は、<xref:System.ServiceModel.Channels.CustomBinding> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="ed0f4-104">すべてのバインディングは、バインド要素の順序付き集合から作成されます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="ed0f4-105">カスタム バインドは、一連のシステム指定のバインド要素から作成したり、ユーザー定義のカスタム バインド要素を含めたりできます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="ed0f4-106">カスタム バインド要素を使用すると、たとえば、新しいトランスポートまたはエンコーダーをサービス エンドポイントで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="ed0f4-107">実施例については、次を参照してください。[カスタム バインディングのサンプル](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08)です。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-107">For working examples, see [Custom Binding Samples](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ed0f4-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ed0f4-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="ed0f4-109">カスタム バインドの構築</span><span class="sxs-lookup"><span data-stu-id="ed0f4-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="ed0f4-110">カスタム バインディングは、特定の順序で "積み重ねられている" バインディング要素のコレクションから <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> コンストラクターを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="ed0f4-111">最上位にあるのは、トランザクションのフローを可能にするオプションの <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> クラスです。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="ed0f4-112">その次にあるのは、WS-ReliableMessaging 仕様で定義されているセッションおよび順序指定のメカニズムを提供する、オプションの <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> クラスです。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="ed0f4-113">セッションは、SOAP 中継局およびトランスポート中継局を通過できます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="ed0f4-114">その次には、承認、認証、保護、機密性などのセキュリティ機能を提供する、オプションの <xref:System.ServiceModel.Channels.SecurityBindingElement> クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
-   <span data-ttu-id="ed0f4-115">その次には、二重通信をネイティブでサポートしないトランスポート プロトコル (HTTP など) を使用して双方向の二重通信を可能にする、オプションの <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
-   <span data-ttu-id="ed0f4-116">その次には、一方向通信を提供する、オプションの <xref:System.ServiceModel.Channels.OneWayBindingElement> クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
-   <span data-ttu-id="ed0f4-117">その次にあるのは、オプションのストリーム セキュリティ バインド要素で、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="ed0f4-118">その次にあるのは、必須のメッセージ エンコード バインド要素です。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="ed0f4-119">独自のメッセージ エンコーダーを使用するか、次の 3 つのメッセージ エンコーディング バインディングのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="ed0f4-120">最下位には、必須のトランスポート要素があります。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="ed0f4-121">独自のトランスポートを使用することも、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] が提供する次のトランスポート バインド要素のいずれかを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-121">You can use your own transport or one of the following transport binding elements [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides:</span></span>  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="ed0f4-122">各層のオプションの概要を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="ed0f4-123">レイヤー</span><span class="sxs-lookup"><span data-stu-id="ed0f4-123">Layer</span></span>|<span data-ttu-id="ed0f4-124">オプション</span><span class="sxs-lookup"><span data-stu-id="ed0f4-124">Options</span></span>|<span data-ttu-id="ed0f4-125">必須</span><span class="sxs-lookup"><span data-stu-id="ed0f4-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="ed0f4-126">トランザクション</span><span class="sxs-lookup"><span data-stu-id="ed0f4-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="ed0f4-127">×</span><span class="sxs-lookup"><span data-stu-id="ed0f4-127">No</span></span>|  
|<span data-ttu-id="ed0f4-128">信頼性</span><span class="sxs-lookup"><span data-stu-id="ed0f4-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="ed0f4-129">Ｘ</span><span class="sxs-lookup"><span data-stu-id="ed0f4-129">No</span></span>|  
|<span data-ttu-id="ed0f4-130">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ed0f4-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="ed0f4-131">×</span><span class="sxs-lookup"><span data-stu-id="ed0f4-131">No</span></span>|  
|<span data-ttu-id="ed0f4-132">エンコード</span><span class="sxs-lookup"><span data-stu-id="ed0f4-132">Encoding</span></span>|<span data-ttu-id="ed0f4-133">テキスト、バイナリ、MTOM (Message Transmission Optimization Mechanism)、カスタム</span><span class="sxs-lookup"><span data-stu-id="ed0f4-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="ed0f4-134">[はい]</span><span class="sxs-lookup"><span data-stu-id="ed0f4-134">Yes</span></span>|  
|<span data-ttu-id="ed0f4-135">Transport</span><span class="sxs-lookup"><span data-stu-id="ed0f4-135">Transport</span></span>|<span data-ttu-id="ed0f4-136">TCP、HTTP、HTTPS、名前付きパイプ (IPC)、ピアツーピア (P2P)、メッセージ キュー (MSMQ)、カスタム</span><span class="sxs-lookup"><span data-stu-id="ed0f4-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="ed0f4-137">[はい]</span><span class="sxs-lookup"><span data-stu-id="ed0f4-137">Yes</span></span>|  
  
 <span data-ttu-id="ed0f4-138">さらに、独自のバインド要素を定義し、それを定義済みの層のいずれかの間に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="ed0f4-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0f4-139">参照</span><span class="sxs-lookup"><span data-stu-id="ed0f4-139">See Also</span></span>  
 [<span data-ttu-id="ed0f4-140">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="ed0f4-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="ed0f4-141">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="ed0f4-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="ed0f4-142">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="ed0f4-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="ed0f4-143">方法 : システム指定のバインディングをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ed0f4-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [<span data-ttu-id="ed0f4-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ed0f4-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="ed0f4-145">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="ed0f4-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
