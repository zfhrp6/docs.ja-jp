---
title: "HTTP、TCP、または名前付きパイプを使用した同期シナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2e40669baadf27ee8d10d84961f27bfea3c997d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="8afe4-102">HTTP、TCP、または名前付きパイプを使用した同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="8afe4-102">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>
<span data-ttu-id="8afe4-103">ここでは、シングル スレッド クライアントで HTTP、TCP、または名前付きパイプを使用したときの、さまざまな同期要求/応答シナリオでのアクティビティと転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-103">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="8afe4-104">参照してください[HTTP、TCP、または名前付きパイプを使用して非同期シナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md)マルチ スレッドの要求についての詳細。</span><span class="sxs-lookup"><span data-stu-id="8afe4-104">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="8afe4-105">エラーを伴わない同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="8afe4-105">Synchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="8afe4-106">ここでは、シングル スレッド クライアントを使用したときの、有効な同期要求/応答シナリオでのアクティビティおよび転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-106">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="8afe4-107">クライアント</span><span class="sxs-lookup"><span data-stu-id="8afe4-107">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="8afe4-108">サービス エンドポイントとの通信の確立</span><span class="sxs-lookup"><span data-stu-id="8afe4-108">Establishing Communication with Service Endpoint</span></span>  
 <span data-ttu-id="8afe4-109">クライアントを構築して開きます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-109">A client is constructed and opened.</span></span> <span data-ttu-id="8afe4-110">各手順は、アンビエント アクティビティ (A) が、「クライアントの構築」(B) と「クライアントを開く」アクティビティ (C) にそれぞれ転送されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-110">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="8afe4-111">転送されるアクティビティごとに、転送が返されるまで (つまり、ServiceModel コードが実行されるまで) アンビエント アクティビティは中断されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-111">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="8afe4-112">サービス エンドポイントへの要求</span><span class="sxs-lookup"><span data-stu-id="8afe4-112">Making a Request to Service Endpoint</span></span>  
 <span data-ttu-id="8afe4-113">アンビエント アクティビティは、(D) アクションを「処理」アクティビティに転送されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-113">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="8afe4-114">このアクティビティでは、要求メッセージが送信され、応答メッセージが受信されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-114">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="8afe4-115">このアクティビティは、ユーザー コードに制御が戻ると終了します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-115">The activity ends when control returns to user code.</span></span> <span data-ttu-id="8afe4-116">これは同期要求であるため、制御が戻るまでアンビエント アクティビティは中断されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-116">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="8afe4-117">サービス エンドポイントとの通信の終了</span><span class="sxs-lookup"><span data-stu-id="8afe4-117">Closing Communication with Service Endpoint</span></span>  
 <span data-ttu-id="8afe4-118">クライアントの "閉じる" アクティビティ (I) が、アンビエント アクティビティから作成されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-118">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="8afe4-119">これは、"新規" や "開く" と同じです。</span><span class="sxs-lookup"><span data-stu-id="8afe4-119">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="8afe4-120">サーバー</span><span class="sxs-lookup"><span data-stu-id="8afe4-120">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="8afe4-121">サービス ホストの設定</span><span class="sxs-lookup"><span data-stu-id="8afe4-121">Setting up a Service Host</span></span>  
 <span data-ttu-id="8afe4-122">ServiceHost の "新規" アクティビティ (N) および "開く" アクティビティ (O) は、アンビエント アクティビティ (M) から作成されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-122">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="8afe4-123">リスナー アクティビティ (P) は、各リスナーの ServiceHost を開くと作成されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-123">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="8afe4-124">リスナー アクティビティは、待機してデータを受信および処理します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-124">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="8afe4-125">ネットワーク上のデータの受信</span><span class="sxs-lookup"><span data-stu-id="8afe4-125">Receiving Data on the Wire</span></span>  
 <span data-ttu-id="8afe4-126">ネットワーク上でデータが到着すると、受信したデータを処理するには、(Q) を既に存在しない場合、「バイトを受信」アクティビティが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-126">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="8afe4-127">このアクティビティは、接続またはキュー内の複数のメッセージに再使用できます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-127">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="8afe4-128">SOAP アクション メッセージを作成するための十分なデータがある場合、"バイトを受信" アクティビティは "メッセージを処理" アクティビティ (R) を起動します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-128">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="8afe4-129">アクティビティ R では、メッセージ ヘッダーが処理され、アクティビティ ID ヘッダーが確認されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-129">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="8afe4-130">このヘッダーが存在する場合、アクティビティ ID は "アクションを処理" アクティビティに設定されます。それ以外の場合は、新しい ID が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-130">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="8afe4-131">呼び出しが処理されると、"アクションを処理" アクティビティ (S) が作成されて転送されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-131">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="8afe4-132">このアクティビティは、受信メッセージに関連するすべての処理 ("ユーザー コードを実行" (T) と "応答メッセージを送信" (該当する場合) を含む) が完了すると終了します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-132">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="8afe4-133">サービス ホストの終了</span><span class="sxs-lookup"><span data-stu-id="8afe4-133">Closing a Service Host</span></span>  
 <span data-ttu-id="8afe4-134">ServiceHost の "閉じる" アクティビティ (Z) は、アンビエント アクティビティから作成されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-134">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 <span data-ttu-id="8afe4-135">![#47; (&)、HTTP を使用した同期のシナリオTCP である (、&) #47 です。名前付きパイプ](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "同期")</span><span class="sxs-lookup"><span data-stu-id="8afe4-135">![Synchronous scenarios using HTTP&#47;TCP&#47; Named Pipes](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "Sync")</span></span>  
  
 <span data-ttu-id="8afe4-136">\<A: name >、`A`はアクティビティとテーブル 3 に、前の説明を表すショートカット シンボルです。</span><span class="sxs-lookup"><span data-stu-id="8afe4-136">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="8afe4-137">`Name` は、アクティビティの短縮名です。</span><span class="sxs-lookup"><span data-stu-id="8afe4-137">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="8afe4-138">場合`propagateActivity` = `true`、プロセス アクション、クライアントとサービスの両方で同じアクティビティ ID を持ちます</span><span class="sxs-lookup"><span data-stu-id="8afe4-138">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="8afe4-139">エラーを伴う同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="8afe4-139">Synchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="8afe4-140">前述のシナリオとの違いは、応答メッセージとして SOAP エラー メッセージが返されることだけです。</span><span class="sxs-lookup"><span data-stu-id="8afe4-140">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="8afe4-141">場合`propagateActivity` = `true`、要求メッセージのアクティビティ ID が SOAP エラー メッセージに追加します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-141">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="8afe4-142">エラーを伴わない同期一方向</span><span class="sxs-lookup"><span data-stu-id="8afe4-142">Synchronous One-Way without Errors</span></span>  
 <span data-ttu-id="8afe4-143">最初のシナリオとの違いは、メッセージがサーバーに返されないことだけです。</span><span class="sxs-lookup"><span data-stu-id="8afe4-143">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="8afe4-144">HTTP ベースのプロトコルの場合は、ステータス (有効またはエラー) がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="8afe4-144">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="8afe4-145">それは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] プロトコル スタックのなかで HTTP プロトコルだけが、要求/応答セマンティクスを使用するからです。</span><span class="sxs-lookup"><span data-stu-id="8afe4-145">This is because HTTP is the only protocol with a request-response semantics that is part of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] protocol stack.</span></span> <span data-ttu-id="8afe4-146">TCP 処理は [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] からは見えないため、受信確認はクライアントに送信されません。</span><span class="sxs-lookup"><span data-stu-id="8afe4-146">Because TCP processing is hidden from [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="8afe4-147">エラーを伴う同期一方向</span><span class="sxs-lookup"><span data-stu-id="8afe4-147">Synchronous One-Way with Errors</span></span>  
 <span data-ttu-id="8afe4-148">メッセージの処理中 (Q 以降) にエラーが発生しても、クライアントには通知が返されません。</span><span class="sxs-lookup"><span data-stu-id="8afe4-148">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="8afe4-149">これは、「エラーを伴わない同期一方向要求/応答」のシナリオと同じです。</span><span class="sxs-lookup"><span data-stu-id="8afe4-149">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="8afe4-150">エラー メッセージを受信する必要がある場合は、一方向のシナリオを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8afe4-150">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="8afe4-151">二重</span><span class="sxs-lookup"><span data-stu-id="8afe4-151">Duplex</span></span>  
 <span data-ttu-id="8afe4-152">上述のシナリオとの違いは、クライアントがサービスとして動作することです。この場合、非同期のシナリオと同様、クライアントは "バイトを受信" アクティビティと "メッセージを処理" アクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="8afe4-152">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
