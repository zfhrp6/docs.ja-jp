---
title: "アクティビティ ID の伝達"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c61087102148688678d868ce25a9cb63315ed65
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="activity-id-propagation"></a><span data-ttu-id="6e855-102">アクティビティ ID の伝達</span><span class="sxs-lookup"><span data-stu-id="6e855-102">Activity ID Propagation</span></span>
<span data-ttu-id="6e855-103">伝達は、ServiceModel アクティビティ トレースが有効な場合 (ServiceModel 伝達) または無効な場合 (ユーザーからユーザーへのアクティビティ伝達) に実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-103">Propagation happens when ServiceModel activity tracing is enabled (ServiceModel propagation) or disabled (User-to-User activity propagation).</span></span>  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a><span data-ttu-id="6e855-104">ServiceModel アクティビティ トレースが有効な場合</span><span class="sxs-lookup"><span data-stu-id="6e855-104">ServiceModel Activity Tracing is Enabled</span></span>  
 <span data-ttu-id="6e855-105">ServiceModel アクティビティ トレースが有効な場合、伝達は ProcessAction アクティビティ間で実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-105">If ServiceModel ActivityTracing is enabled, propagation happens between ProcessAction activities.</span></span>  
  
### <a name="server"></a><span data-ttu-id="6e855-106">サーバー</span><span class="sxs-lookup"><span data-stu-id="6e855-106">Server</span></span>  
 <span data-ttu-id="6e855-107">ときに、`propagateActivity`属性に設定されている`true`クライアントとサーバーの ID の両方で、 `ProcessAction` 、サーバーのアクティビティは伝達された ID と同じ`ActivityId`メッセージ ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="6e855-107">When the `propagateActivity` attribute is set to `true` on both the client and server, the ID of the `ProcessAction` activity in the server is identical to the ID in the propagated `ActivityId` message header.</span></span>  
  
 <span data-ttu-id="6e855-108">ない場合`ActivityId`ヘッダーがメッセージに存在 (つまり、 `propagateActivity` = `false`クライアントで)、または`propagateActivity` = `false`サーバーをサーバー上には、新しいアクティビティ ID を生成します</span><span class="sxs-lookup"><span data-stu-id="6e855-108">When no `ActivityId` header is present in the message (that is, `propagateActivity`=`false` on the client), or when `propagateActivity`=`false` on the server, the server generates a new activity ID.</span></span>  
  
### <a name="client"></a><span data-ttu-id="6e855-109">クライアント</span><span class="sxs-lookup"><span data-stu-id="6e855-109">Client</span></span>  
 <span data-ttu-id="6e855-110">クライアントが同期的にシングル スレッドで動作する場合、クライアントは、クライアントまたはサーバー側で `propagateActivity` の設定を無視します。</span><span class="sxs-lookup"><span data-stu-id="6e855-110">If the client is synchronously single threaded, the client disregards any settings of `propagateActivity` at the client or server.</span></span> <span data-ttu-id="6e855-111">代わりに、応答は要求アクティビティで処理されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-111">Instead, the response is handled in the request activity.</span></span> <span data-ttu-id="6e855-112">クライアントが非同期的または同期の場合、マルチ スレッド`propagateActivity` = `true`クライアントで、サーバーによって送信されたメッセージにアクティビティ ID ヘッダーがあると、クライアントが、メッセージからアクティビティ ID を取得しに転送、Process Action アクティビティ伝達されたアクティビティ ID を含む</span><span class="sxs-lookup"><span data-stu-id="6e855-112">If the client is asynchronous or synchronous multithreaded, `propagateActivity`=`true` in the client, and there is an activity ID header in the message sent by the server, the client retrieves the activity ID from the message, and transfers to the Process Action activity that contains the propagated activity ID.</span></span> <span data-ttu-id="6e855-113">それ以外の場合、クライアントは、"プロセス メッセージ" アクティビティから新しい "プロセス アクション" アクティビティに転送します。</span><span class="sxs-lookup"><span data-stu-id="6e855-113">Otherwise, the client transfers from Process Message activity to a new Process Action activity.</span></span> <span data-ttu-id="6e855-114">この新しい "プロセス アクション" アクティビティへの転送は、整合性を維持するために行われます。</span><span class="sxs-lookup"><span data-stu-id="6e855-114">This extra transfer to a new Process Action activity is done for consistency.</span></span> <span data-ttu-id="6e855-115">このアクティビティの内部で、クライアントは、スレッドが応答メッセージ処理用に割り当てられている場合、ローカル スレッド コンテキストから BeginCall アクティビティのアクティビティ ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e855-115">Inside this activity, the client retrieves the activity ID of the BeginCall activity from the local thread context, when the thread is allocated for response message processing.</span></span> <span data-ttu-id="6e855-116">その後、最初の "プロセス アクション" アクティビティに転送します。</span><span class="sxs-lookup"><span data-stu-id="6e855-116">It then transfers to the initial Process Action activity.</span></span>  
  
 <span data-ttu-id="6e855-117">クライアントが双方向の場合、クライアントは、メッセージを受信するときにサーバーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="6e855-117">If the client is duplex, the client acts as server on receiving the message.</span></span>  
  
### <a name="propagation-in-fault-messages"></a><span data-ttu-id="6e855-118">エラー メッセージの伝達</span><span class="sxs-lookup"><span data-stu-id="6e855-118">Propagation in Fault Messages</span></span>  
 <span data-ttu-id="6e855-119">有効なメッセージの処理とエラー メッセージの処理に違いはありません。</span><span class="sxs-lookup"><span data-stu-id="6e855-119">There is no difference in handling valid and fault messages.</span></span> <span data-ttu-id="6e855-120">場合`propagateActivity` = `true`、SOAP エラー メッセージのヘッダーに追加されたアクティビティ ID は、アンビエント アクティビティと同じです。</span><span class="sxs-lookup"><span data-stu-id="6e855-120">If `propagateActivity`=`true`, the activity ID added to the SOAP fault message headers is identical to the ambient activity.</span></span>  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a><span data-ttu-id="6e855-121">ServiceModel アクティビティ トレースが無効な場合</span><span class="sxs-lookup"><span data-stu-id="6e855-121">ServiceModel Activity Tracing is Disabled</span></span>  
 <span data-ttu-id="6e855-122">ServiceModel アクティビティ トレースが無効な場合、伝達は、ServiceModel アクティビティを通過せずに直接ユーザー コード アクティビティ間で実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-122">If ServiceModel ActivityTracing is disabled, propagation occurs between user code activities directly without going through ServiceModel activities.</span></span> <span data-ttu-id="6e855-123">ユーザー定義のアクティビティ ID もメッセージ アクティビティ ID ヘッダーによって伝達されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-123">A user-defined activity ID is also propagated through the message activity ID header.</span></span>  
  
 <span data-ttu-id="6e855-124">場合`propagateActivity` = `true`と`ActivityTracing` = `off` (ServiceModel のトレースを有効かどうか) に関係なく、ServiceModel トレース リスナーの次は、クライアントまたはサーバーで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e855-124">If `propagateActivity`=`true` and `ActivityTracing`=`off` for a ServiceModel trace listener (regardless of whether tracing is enabled on ServiceModel), the following happen on either the client or server:</span></span>  
  
-   <span data-ttu-id="6e855-125">要求の処理時または応答の送信時に、TLS のアクティビティ ID は、メッセージが作成されるまでユーザー コードの外部で伝達されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-125">On operation request or sending response, the activity ID in TLS is propagated out of user code until a message is formed.</span></span> <span data-ttu-id="6e855-126">また、アクティビティ ID ヘッダーは、メッセージが送信される前にメッセージに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-126">An activity ID header is also inserted into the message before it is sent.</span></span>  
  
-   <span data-ttu-id="6e855-127">要求の受信時または応答の受信時に、アクティビティ ID は、受信したメッセージのオブジェクトが作成されしだい、メッセージ ヘッダーから取得されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-127">On receiving request or receiving response, the activity ID is retrieved from the message header as soon as the received message object is created.</span></span> <span data-ttu-id="6e855-128">TLS のアクティビティ ID は、メッセージがスコープから消えるとすぐに、ユーザー コードに到達するまで伝達されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-128">The activity ID in TLS is propagated as soon as the message disappears from scope until user code is reached.</span></span>  
  
 <span data-ttu-id="6e855-129">このアクションによって、伝達が有効な場合にユーザー トレースが同じアクティビティに表示されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-129">These actions guarantee that user traces will appear in the same activity if propagation is on.</span></span> <span data-ttu-id="6e855-130">ただし、ServiceModel トレースに対する保証はありません。</span><span class="sxs-lookup"><span data-stu-id="6e855-130">However, it makes no guarantee on ServiceModel traces.</span></span> <span data-ttu-id="6e855-131">ServiceModel トレースは、このトレースの処理がユーザー コード アクティビティが設定されたのと同じスレッドで実行される場合のみ、ユーザー コード アクティビティで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-131">ServiceModel traces occur in a user code activity only if the processing of those traces is executed on the same thread where the user code activity was set.</span></span>  
  
 <span data-ttu-id="6e855-132">通常、ServiceModel トレースは、次の場所で確認できます。</span><span class="sxs-lookup"><span data-stu-id="6e855-132">In general, ServiceModel traces can be observed in the following places:</span></span>  
  
-   <span data-ttu-id="6e855-133">ServiceModel トレースが無効な場合、出力されたすべてのトレースは、ユーザー アクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-133">If ServiceModel tracing is disabled, all emitted traces appear in user activities.</span></span> <span data-ttu-id="6e855-134">サーバーとクライアントの両方で伝達が有効な場合、このトレースは同じアクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-134">If propagation is enabled at both the server and client, these traces will be in the same activity.</span></span>  
  
-   <span data-ttu-id="6e855-135">ServiceModel トレースが有効で、ActivityTracing が無効の場合、ユーザー トレースは、サーバーとクライアントの両方で伝達が有効な場合は同じアクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-135">If ServiceModel tracing is enabled, but ActivityTracing is disabled, user traces appear in the same activity if propagation is enabled on both ends.</span></span> <span data-ttu-id="6e855-136">ServiceModel トレースは、既定の 0000 アクティビティに表示されます。ただし、このトレースが、アクティビティが最初に設定されたユーザー コード処理と同じスレッドで実行される場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="6e855-136">ServiceModel traces appear in the default 0000 activity, unless they occur in the same thread as the user code processing where the activity is initially set.</span></span>  
  
-   <span data-ttu-id="6e855-137">ServiceModel トレースと ActivityTracing が両方とも有効な場合、ユーザー トレースは、ユーザー定義のアクティビティに表示され、ServiceModel トレースは、ServiceModel 定義のアクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-137">If both ServiceModel tracing and ActivityTracing are enabled, user traces appear in user-defined activities, and ServiceModel traces appear in ServiceModel-defined activities.</span></span> <span data-ttu-id="6e855-138">伝達は、ServiceModel レベルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e855-138">Propagation happens at ServiceModel level.</span></span>
