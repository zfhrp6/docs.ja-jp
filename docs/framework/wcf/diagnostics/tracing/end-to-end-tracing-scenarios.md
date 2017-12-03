---
title: "エンドツーエンドのトレースのシナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f83b7d53-6061-4362-a9a3-ee1daf6542be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33f576b177ddb66d6145e0b1a5d0d104346640ee
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="end-to-end-tracing-scenarios"></a><span data-ttu-id="246cd-102">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="246cd-102">End-To-End Tracing Scenarios</span></span>
<span data-ttu-id="246cd-103">このセクションの各トピックで、トレースの使用に関するさまざまなシナリオを説明します。</span><span class="sxs-lookup"><span data-stu-id="246cd-103">This section contains topics that describe different scenarios for using tracing.</span></span>  
  
 <span data-ttu-id="246cd-104">要求/応答、一方向、双方向の各シナリオで、アクティビティ トレースを次の方法で実装します。</span><span class="sxs-lookup"><span data-stu-id="246cd-104">Activity Tracing is implemented for Reply/Response, OneWay and Duplex scenarios using the following</span></span>  
  
-   <span data-ttu-id="246cd-105">同期または非同期</span><span class="sxs-lookup"><span data-stu-id="246cd-105">Synchronous or Asynchronous</span></span>  
  
-   <span data-ttu-id="246cd-106">BasicHttpBinding、netNamedPipeBinding、netTcpBinding、wsHttpBinding、または netMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="246cd-106">BasicHttpBinding, netNamedPipeBinding, netTcpBinding, wsHttpBinding or netMsmqBinding</span></span>  
  
-   <span data-ttu-id="246cd-107">COM サービス</span><span class="sxs-lookup"><span data-stu-id="246cd-107">COM Service</span></span>  
  
-   <span data-ttu-id="246cd-108">ユーザー アクティビティ ID の伝達</span><span class="sxs-lookup"><span data-stu-id="246cd-108">User activity id propagation</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="246cd-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="246cd-109">In This Section</span></span>  
  
-   [<span data-ttu-id="246cd-110">アクティビティ リスト</span><span class="sxs-lookup"><span data-stu-id="246cd-110">Activity List</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)  
  
-   [<span data-ttu-id="246cd-111">アクティビティ ID の伝達</span><span class="sxs-lookup"><span data-stu-id="246cd-111">Activity ID Propagation</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/activity-id-propagation.md)  
  
-   [<span data-ttu-id="246cd-112">HTTP、TCP または名前付きパイプを使用した同期のシナリオ</span><span class="sxs-lookup"><span data-stu-id="246cd-112">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/synchronous-scenarios-using-http-tcp-or-named-pipe.md)  
  
-   [<span data-ttu-id="246cd-113">HTTP、TCP、または名前付きパイプを使用して非同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="246cd-113">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md)  
  
-   [<span data-ttu-id="246cd-114">メッセージ セキュリティにおけるアクティビティ トレース</span><span class="sxs-lookup"><span data-stu-id="246cd-114">Activity Tracing in Message Security</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/activity-tracing-in-message-security.md)  
  
-   [<span data-ttu-id="246cd-115">MSMQ</span><span class="sxs-lookup"><span data-stu-id="246cd-115">MSMQ</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/msmq.md)  
  
-   [<span data-ttu-id="246cd-116">COM +</span><span class="sxs-lookup"><span data-stu-id="246cd-116">COM+</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/com.md)  
  
## <a name="see-also"></a><span data-ttu-id="246cd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="246cd-117">See Also</span></span>  
 [<span data-ttu-id="246cd-118">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="246cd-118">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="246cd-119">エンド ツー エンドのトレース</span><span class="sxs-lookup"><span data-stu-id="246cd-119">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
