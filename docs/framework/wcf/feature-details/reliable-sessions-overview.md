---
title: "信頼できるセッションの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d2749188214f3f68ee3ed5df87fc0aa7cac604d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-sessions-overview"></a><span data-ttu-id="c1aa5-102">信頼できるセッションの概要</span><span class="sxs-lookup"><span data-stu-id="c1aa5-102">Reliable Sessions Overview</span></span>

[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="c1aa5-103"> の SOAP リライアブル メッセージ機能では、SOAP エンドポイント間でエンドツーエンドのメッセージ転送に信頼性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-103"> SOAP reliable messaging provides end-to-end message transfer reliability between SOAP endpoints.</span></span> <span data-ttu-id="c1aa5-104">これにより、信頼性の低いネットワーク上でも、トランスポート エラーや SOAP メッセージ レベルのエラーに対処できます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-104">It does this on networks that are unreliable by overcoming transport failures and SOAP message-level failures.</span></span> <span data-ttu-id="c1aa5-105">具体的には、SOAP またはトランスポート中継局を経由して送信されるメッセージに関して、1 回だけの配信や (オプションで) 順序保証の配信がセッション ベースで提供されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-105">In particular, it provides session-based, single, and (optionally) ordered delivery for messages sent across SOAP or transport intermediaries.</span></span> <span data-ttu-id="c1aa5-106">セッション ベースの配布は、メッセージの省略可能な順序とのセッションでメッセージをグループ化を提供します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-106">Session-based delivery provides for grouping messages in a session with optional ordering of the messages.</span></span>

<span data-ttu-id="c1aa5-107">このトピックでは、信頼できるセッションをする方法について説明と、使用するタイミングと方法をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-107">This topic describes reliable sessions, how and when to use them, and how to secure them.</span></span>

## <a name="wcf-reliable-sessions"></a><span data-ttu-id="c1aa5-108">WCF の信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="c1aa5-108">WCF reliable sessions</span></span>

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c1aa5-109"> の信頼できるセッションは、WS-ReliableMessaging プロトコルの定義に準拠した SOAP リライアブル メッセージ機能の実装です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-109"> reliable sessions is an implementation of SOAP reliable messaging as defined by the WS-ReliableMessaging protocol.</span></span>

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c1aa5-110"> の SOAP リライアブル メッセージ機能は、メッセージング エンドポイントを分離する中継局の数や種類に関係なく、2 つのエンドポイント間でエンドツーエンドの信頼できるセッションを実現します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-110"> SOAP reliable messaging provides an end-to-end reliable session between two endpoints, regardless of the number or type of intermediaries that separate the messaging endpoints.</span></span> <span data-ttu-id="c1aa5-111">これにより、SOAP (HTTP プロキシなど) を使用しないトランスポート手段が含まれます。 や中継ぎ局 SOAP (たとえば、SOAP ベースのルーターやブリッジなど) を使用するエンドポイントの間でメッセージを必要とされます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-111">This includes any transport intermediaries that don't use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="c1aa5-112">信頼できるセッション チャネルをサポートしている*インタラクティブ*通信できるように、このようなチャネルが接続されているサービスが同時に実行し、低待機時間、つまりの条件下でメッセージを処理内で比較的短い時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-112">A reliable session channel supports *interactive* communication so that the services connected by such a channel run concurrently and exchange and process messages under conditions of low latency, that is, within relatively short intervals of time.</span></span> <span data-ttu-id="c1aa5-113">この組み合わせは、それらの間で提供される分離がないように、これらのコンポーネントは一緒に進めるか、ひとまとまりでフェールオーバーを意味します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-113">This coupling means that these components make progress together or fail together, so there's no isolation provided between them.</span></span>

<span data-ttu-id="c1aa5-114">信頼できるセッションでは次の 2 種類のエラーがマスクされます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-114">A reliable session masks two kinds of failures:</span></span>

- <span data-ttu-id="c1aa5-115">SOAP メッセージ レベルのエラー (メッセージの喪失または重複、および送信順序と異なる順序で到着するメッセージを含む)</span><span class="sxs-lookup"><span data-stu-id="c1aa5-115">SOAP message-level failures, which includes lost or duplicated messages and messages that arrive in a different order from the order in which they were sent.</span></span>

- <span data-ttu-id="c1aa5-116">トランスポート エラー</span><span class="sxs-lookup"><span data-stu-id="c1aa5-116">Transport failures.</span></span>

<span data-ttu-id="c1aa5-117">信頼できるセッションは、WS-ReliableMessaging プロトコルとメモリ内転送ウィンドウを実装することにより、トランスポート エラーが発生した場合に SOAP メッセージ レベルのエラーをマスクし、接続を再確立します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-117">A reliable session implements the WS-ReliableMessaging protocol and an in-memory transfer window to mask SOAP message-level failures and re-establishes connections in the case of transport failures.</span></span>

<span data-ttu-id="c1aa5-118">信頼できるセッションは、TCP が IP パケットに提供する信頼性を SOAP メッセージに提供します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-118">A reliable session provides for SOAP messages what TCP provides for IP packets.</span></span> <span data-ttu-id="c1aa5-119">TCP ソケット接続では、ノード間で IP パケットが 1 回のみ、正しい順序で転送されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-119">A TCP socket connection provides a singular, in-order transfer of IP packets between nodes.</span></span> <span data-ttu-id="c1aa5-120">信頼できるチャネルでも、これと同じタイプの信頼できる転送が提供されますが、次の点で TCP ソケットの信頼性とは異なります。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-120">The reliable channel provides the same type of reliable transfer, but it differs from TCP socket reliability in the following ways:</span></span>

- <span data-ttu-id="c1aa5-121">信頼性は、任意のサイズのバイト パケットに対してではなく、SOAP メッセージ レベルで提供されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-121">The reliability is at the SOAP message level, not for an arbitrarily sized packet of bytes.</span></span>

- <span data-ttu-id="c1aa5-122">信頼性はトランスポート中立 TCP 経由する転送に対してだけでなく提供されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-122">The reliability is transport-neutral, not just for transfer over TCP.</span></span>

- <span data-ttu-id="c1aa5-123">信頼性の特定のトランスポート セッション (たとえば、TCP 接続により、セッション) に関連付けられていない使用できると複数のトランスポート セッション順番にまたは同時に信頼できるセッションの有効期間。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-123">The reliability isn't tied to a particular transport session (for example, the session a TCP connection provides) and can use multiple transport sessions concurrently or sequentially over the lifetime of the reliable session.</span></span>

- <span data-ttu-id="c1aa5-124">信頼できるセッションは、送信側と受信側の SOAP エンドポイント間の接続に必要なトランスポート接続の数に関係なく、両者の間で提供されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-124">The reliable session is between the sender and receiver SOAP endpoints, regardless of the number of transport connections required for connectivity between them.</span></span> <span data-ttu-id="c1aa5-125">つまり、TCP の信頼性はトランスポート接続が終了する、エンド ツー エンドの信頼性を提供しますが、信頼できるセッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-125">In short, TCP reliability ends where the transport connection ends, while a reliable session provides end-to-end reliability.</span></span>

## <a name="reliable-sessions-and-bindings"></a><span data-ttu-id="c1aa5-126">信頼できるセッションとバインディング</span><span class="sxs-lookup"><span data-stu-id="c1aa5-126">Reliable sessions and bindings</span></span>

<span data-ttu-id="c1aa5-127">前述のように、信頼できるセッションは、トランスポート中立的なです。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-127">As mentioned earlier, a reliable session is transport neutral.</span></span> <span data-ttu-id="c1aa5-128">また、要求/応答や双方向など、複数のメッセージ交換パターンで信頼できるセッションを確立することができます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-128">Also, you can establish a reliable session over many message exchange patterns, such as request-reply or duplex.</span></span> <span data-ttu-id="c1aa5-129">A[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]信頼できるセッションは、一連のバインドのプロパティとして公開します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-129">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reliable session is exposed as a property of a set of bindings.</span></span>

<span data-ttu-id="c1aa5-130">使用するエンドポイントでは、信頼できるセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-130">Use a reliable session on endpoints that use:</span></span>

- <span data-ttu-id="c1aa5-131">HTTP ベース トランスポートの標準バインディング</span><span class="sxs-lookup"><span data-stu-id="c1aa5-131">HTTP-based transport standard bindings:</span></span>

  - <span data-ttu-id="c1aa5-132">`WsHttpBinding` : 要求/応答または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-132">`WsHttpBinding` and expose request-reply or one-way contracts.</span></span>

  - <span data-ttu-id="c1aa5-133">ときに、要求/応答または一方向のサービス コントラクト上で信頼できるセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-133">When using reliable session over a request-reply or simple one-way service contract.</span></span>

  - <span data-ttu-id="c1aa5-134">`WsDualHttpBinding` : 双方向、要求/応答、または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-134">`WsDualHttpBinding` and expose duplex, request-reply, or one-way contracts.</span></span>

  - <span data-ttu-id="c1aa5-135">`WsFederationHttpBinding` : 要求/応答または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-135">`WsFederationHttpBinding` and expose request-reply or one-way contracts.</span></span>

- <span data-ttu-id="c1aa5-136">TCP ベース トランスポートの標準バインディング</span><span class="sxs-lookup"><span data-stu-id="c1aa5-136">TCP-based transport standard bindings:</span></span>

  - <span data-ttu-id="c1aa5-137">`NetTcpBinding` : 双方向、要求/応答、または一方向のコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-137">`NetTcpBinding` and expose duplex, request reply, or one-way contracts.</span></span>

<span data-ttu-id="c1aa5-138">HTTPS などのカスタム バインディングを作成することで、他のバインディングの信頼できるセッションを使用して (に関する問題の詳細については、次を参照してください。<a href="#reliable-sessions-and-security">信頼できるセッションとセキュリティ</a>) または名前付きパイプ バインドします。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-138">Use a reliable session on any other bindings by creating a custom binding, such as HTTPS (for more information about issues, see <a href="#reliable-sessions-and-security">Reliable sessions and security</a>) or a named pipe binding.</span></span>

<span data-ttu-id="c1aa5-139">基になるチャネルの種類別、上の信頼できるセッションを積み重ねることができ、結果として得られる、信頼できるセッション チャネル形状が変化します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-139">You can stack a reliable session on different underlying channel types, and the resulting reliable session channel shape varies.</span></span> <span data-ttu-id="c1aa5-140">クライアントとサーバーの両方でサポートされている信頼できるセッション チャネルの種類は、使用される基になるチャネルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-140">On both the client and the server, the type of reliable session channel supported depends on the type of underlying channel used.</span></span> <span data-ttu-id="c1aa5-141">次の表では、基になるチャネルの種類ごとに、クライアントでサポートされるセッション チャネルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-141">The following table lists the types of session channels supported on the client as a function of the underlying channel type.</span></span>

| <span data-ttu-id="c1aa5-142">サポートされている信頼できるセッション チャネルの種類 &#8224;です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-142">Supported reliable session channel types&#8224;</span></span> | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | <span data-ttu-id="c1aa5-143">[はい]</span><span class="sxs-lookup"><span data-stu-id="c1aa5-143">Yes</span></span>               | <span data-ttu-id="c1aa5-144">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-144">Yes</span></span>                      | <span data-ttu-id="c1aa5-145">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-145">Yes</span></span>              | <span data-ttu-id="c1aa5-146">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-146">Yes</span></span>                     |
| `IRequestSessionChannel`                        | <span data-ttu-id="c1aa5-147">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-147">Yes</span></span>               | <span data-ttu-id="c1aa5-148">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-148">Yes</span></span>                      | <span data-ttu-id="c1aa5-149">いいえ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-149">No</span></span>               | <span data-ttu-id="c1aa5-150">Ｘ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-150">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="c1aa5-151">Ｘ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-151">No</span></span>                | <span data-ttu-id="c1aa5-152">Ｘ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-152">No</span></span>                       | <span data-ttu-id="c1aa5-153">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-153">Yes</span></span>              | <span data-ttu-id="c1aa5-154">[はい]</span><span class="sxs-lookup"><span data-stu-id="c1aa5-154">Yes</span></span>                     |

<span data-ttu-id="c1aa5-155">&#8224;です。サポートされているチャネルの種類は、ジェネリックの使用可能な値`TChannel`に渡されるパラメーター値、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-155">&#8224;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

<span data-ttu-id="c1aa5-156">次の表では、基になるチャネルの種類ごとに、サーバーでサポートされるセッション チャネルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-156">The following table lists the types of session channels supported on the server as a function of the underlying channel type.</span></span>

| <span data-ttu-id="c1aa5-157">サポートされている信頼できるセッション チャネルの種類 &#8225;です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-157">Supported reliable session channel types&#8225;</span></span> | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | <span data-ttu-id="c1aa5-158">[はい]</span><span class="sxs-lookup"><span data-stu-id="c1aa5-158">Yes</span></span>             | <span data-ttu-id="c1aa5-159">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-159">Yes</span></span>                    | <span data-ttu-id="c1aa5-160">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-160">Yes</span></span>              | <span data-ttu-id="c1aa5-161">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-161">Yes</span></span>                     |
| `IReplySessionChannel`                          | <span data-ttu-id="c1aa5-162">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-162">Yes</span></span>             | <span data-ttu-id="c1aa5-163">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-163">Yes</span></span>                    | <span data-ttu-id="c1aa5-164">いいえ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-164">No</span></span>               | <span data-ttu-id="c1aa5-165">Ｘ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-165">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="c1aa5-166">Ｘ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-166">No</span></span>              | <span data-ttu-id="c1aa5-167">Ｘ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-167">No</span></span>                     | <span data-ttu-id="c1aa5-168">はい</span><span class="sxs-lookup"><span data-stu-id="c1aa5-168">Yes</span></span>              | <span data-ttu-id="c1aa5-169">[はい]</span><span class="sxs-lookup"><span data-stu-id="c1aa5-169">Yes</span></span>                     |

<span data-ttu-id="c1aa5-170">&#8225;です。サポートされているチャネルの種類は、ジェネリックの使用可能な値`TChannel`に渡されるパラメーター値、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-170">&#8225;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

## <a name="reliable-sessions-and-security"></a><span data-ttu-id="c1aa5-171">信頼できるセッションとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-171">Reliable sessions and security</span></span>

<span data-ttu-id="c1aa5-172">信頼できるセッションをセキュリティ保護することが重要通信している双方 (サービスとクライアント) が認証されると、セッションで交換されるメッセージが改ざんされないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-172">Securing a reliable session is important to ensure that the communicating parties (service and client) are authenticated and that the messages exchanged in the session aren't tampered with.</span></span> <span data-ttu-id="c1aa5-173">さらに、それぞれ個別の信頼できるセッションの整合性を確保する重要なは。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-173">Furthermore, it's important to ensure the integrity of each individual reliable session.</span></span> <span data-ttu-id="c1aa5-174">信頼できるセッションは、表現があり、セキュリティ セッション チャネルで管理するセキュリティ コンテキストにバインドすることによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-174">A reliable session is secured by binding it to a security context that's represented and managed by a security session channel.</span></span> <span data-ttu-id="c1aa5-175">セキュリティ チャネルによって、セキュリティ セッションが可能になります。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-175">The security channel provides a security session.</span></span> <span data-ttu-id="c1aa5-176">セッション確立中に交換されるセキュリティ トークンは、信頼できるセッションでメッセージをセキュリティで保護するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-176">Security tokens exchanged during the session establishment are then used to secure the messages in the reliable session.</span></span>

<span data-ttu-id="c1aa5-177">信頼できるセッションが TCP-s 上にあるときは、TCP セッションが信頼できるセッションに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-177">When a reliable session is over TCP-S, the TCP session is tied to the reliable session.</span></span> <span data-ttu-id="c1aa5-178">そのため、トランスポート セキュリティにより、セキュリティが信頼できるセッションにも関連付けられていることにします。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-178">Therefore, transport security ensures that security is also tied to the reliable session.</span></span> <span data-ttu-id="c1aa5-179">この場合、接続の再確立は無効になります。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-179">In this case, connection re-establishment is turned off.</span></span>

<span data-ttu-id="c1aa5-180">唯一の例外は、HTTPS の使用時です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-180">The only exception is when using HTTPS.</span></span> <span data-ttu-id="c1aa5-181">Secure Sockets Layer (SSL) セッションは、信頼できるセッションにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-181">The Secure Sockets Layer (SSL) session isn't bound to the reliable session.</span></span> <span data-ttu-id="c1aa5-182">セキュリティ コンテキスト (SSL セッション) を共有しているセッションが; 互いから保護されていないため、脅威は、このこれが原因か、アプリケーションによっては現実的な脅威ができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-182">This imposes a threat because sessions that are sharing a security context (the SSL session) aren't protected from each other; this might or might not be a real threat depending on the application.</span></span>

## <a name="using-reliable-sessions"></a><span data-ttu-id="c1aa5-183">信頼できるセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-183">Using reliable sessions</span></span>

<span data-ttu-id="c1aa5-184">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるセッションを使用するには、信頼できるセッションをサポートするバインディングを使用してエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-184">To use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reliable sessions, create an endpoint with a binding that supports a reliable session.</span></span> <span data-ttu-id="c1aa5-185">システム指定のバインディングのいずれかを使用する[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]有効になっている信頼できるセッションでは、またはこれを行う独自のカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-185">Use one of the system-provided bindings that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides with the reliable session enabled or create your own custom binding that does this.</span></span>

<span data-ttu-id="c1aa5-186">信頼できるセッションが既定でサポートおよび有効化されているシステム定義のバインディングは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-186">The system-defined bindings that support and enable a reliable session by default include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

<span data-ttu-id="c1aa5-187">既定で有効にしないオプションとして、信頼できるセッションをサポートするシステム提供のバインディングは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-187">The system-provided bindings that support a reliable session as an option but don't enable one by default include:</span></span>

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

<span data-ttu-id="c1aa5-188">カスタム バインディングを作成する方法の例は、次を参照してください。[する方法: HTTPS で、カスタムの信頼できるセッション バインドを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-188">For an example of how to create a custom binding, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

<span data-ttu-id="c1aa5-189">については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を信頼できるセッションをサポートするバインディングを参照してください[システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-189">For a discussion of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings that support reliable sessions, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>

## <a name="when-to-use-reliable-sessions"></a><span data-ttu-id="c1aa5-190">信頼できるセッションを使用する場合</span><span class="sxs-lookup"><span data-stu-id="c1aa5-190">When to use reliable sessions</span></span>

<span data-ttu-id="c1aa5-191">アプリケーションで信頼できるセッションを使用するタイミングを理解しておく必要です。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-191">It's important to understand when to use reliable sessions in your application.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c1aa5-192"> では、双方のエンドポイントがどちらもアクティブである場合に、信頼できるセッションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-192"> supports reliable sessions between endpoints that are active and alive at the same time.</span></span> <span data-ttu-id="c1aa5-193">アプリケーションでは、エンドポイントのいずれかが必要な場合は、時間、一定期間使用できないし、信頼性を実現するためにキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-193">If your application requires one of the endpoints be unavailable for a duration of time, then use queues to achieve reliability.</span></span>

<span data-ttu-id="c1aa5-194">シナリオでは、2 つのエンドポイントを TCP 経由で接続されている必要がある場合、TCP は信頼性の高いメッセージ交換を提供するための十分なあります。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-194">If the scenario requires two endpoints connected over TCP, then TCP may be sufficient to provide reliable message exchanges.</span></span> <span data-ttu-id="c1aa5-195">TCP 確実に信頼できるセッションを使用する必要はありませんが、パケットは 1 回だけ、正しい順序で到着します。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-195">Although, it isn't necessary to use a reliable session, since TCP ensures that the packets arrive in order and only once.</span></span>

<span data-ttu-id="c1aa5-196">シナリオでは、次の特性のいずれか、する必要がありますに深刻な使用を検討して、信頼できるセッションです。</span><span class="sxs-lookup"><span data-stu-id="c1aa5-196">If your scenario has any of the following characteristics, then you must seriously consider using a reliable session.</span></span>

- <span data-ttu-id="c1aa5-197">SOAP ルーターなどの SOAP 中継ぎ局</span><span class="sxs-lookup"><span data-stu-id="c1aa5-197">SOAP intermediaries, such as SOAP routers</span></span>

- <span data-ttu-id="c1aa5-198">プロキシ中継ぎ局またはトランスポート ブリッジ</span><span class="sxs-lookup"><span data-stu-id="c1aa5-198">Proxy intermediaries or transport bridges</span></span>

- <span data-ttu-id="c1aa5-199">断続的な接続</span><span class="sxs-lookup"><span data-stu-id="c1aa5-199">Intermittent connectivity</span></span>

- <span data-ttu-id="c1aa5-200">HTTP 経由でセッション</span><span class="sxs-lookup"><span data-stu-id="c1aa5-200">Sessions over HTTP</span></span>

## <a name="see-also"></a><span data-ttu-id="c1aa5-201">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1aa5-201">See also</span></span>

<span data-ttu-id="c1aa5-202">[バインディングを使用してサービスとクライアントを構成するには](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md) </span><span class="sxs-lookup"><span data-stu-id="c1aa5-202">[Using Bindings to Configure Services and Clients](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md) </span></span>  
[<span data-ttu-id="c1aa5-203">WS 信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="c1aa5-203">WS Reliable Session</span></span>](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
