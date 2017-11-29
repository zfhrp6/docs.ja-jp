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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d37f752e0a36835f91e01b7c092b654eeba2b8ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="end-to-end-tracing-scenarios"></a><span data-ttu-id="cd822-102">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="cd822-102">End-To-End Tracing Scenarios</span></span>
<span data-ttu-id="cd822-103">このセクションの各トピックで、トレースの使用に関するさまざまなシナリオを説明します。</span><span class="sxs-lookup"><span data-stu-id="cd822-103">This section contains topics that describe different scenarios for using tracing.</span></span>  
  
 <span data-ttu-id="cd822-104">要求/応答、一方向、双方向の各シナリオで、アクティビティ トレースを次の方法で実装します。</span><span class="sxs-lookup"><span data-stu-id="cd822-104">Activity Tracing is implemented for Reply/Response, OneWay and Duplex scenarios using the following</span></span>  
  
-   <span data-ttu-id="cd822-105">同期または非同期</span><span class="sxs-lookup"><span data-stu-id="cd822-105">Synchronous or Asynchronous</span></span>  
  
-   <span data-ttu-id="cd822-106">BasicHttpBinding、netNamedPipeBinding、netTcpBinding、wsHttpBinding、または netMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="cd822-106">BasicHttpBinding, netNamedPipeBinding, netTcpBinding, wsHttpBinding or netMsmqBinding</span></span>  
  
-   <span data-ttu-id="cd822-107">COM サービス</span><span class="sxs-lookup"><span data-stu-id="cd822-107">COM Service</span></span>  
  
-   <span data-ttu-id="cd822-108">ユーザー アクティビティ ID の伝達</span><span class="sxs-lookup"><span data-stu-id="cd822-108">User activity id propagation</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd822-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cd822-109">In This Section</span></span>  
  
-   [<span data-ttu-id="cd822-110">アクティビティ リスト</span><span class="sxs-lookup"><span data-stu-id="cd822-110">Activity List</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)  
  
-   [<span data-ttu-id="cd822-111">アクティビティ ID の伝達</span><span class="sxs-lookup"><span data-stu-id="cd822-111">Activity ID Propagation</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/activity-id-propagation.md)  
  
-   [<span data-ttu-id="cd822-112">HTTP、TCP または名前付きパイプを使用した同期のシナリオ</span><span class="sxs-lookup"><span data-stu-id="cd822-112">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/synchronous-scenarios-using-http-tcp-or-named-pipe.md)  
  
-   [<span data-ttu-id="cd822-113">HTTP、TCP、または名前付きパイプを使用して非同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="cd822-113">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md)  
  
-   [<span data-ttu-id="cd822-114">メッセージ セキュリティにおけるアクティビティ トレース</span><span class="sxs-lookup"><span data-stu-id="cd822-114">Activity Tracing in Message Security</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/activity-tracing-in-message-security.md)  
  
-   [<span data-ttu-id="cd822-115">MSMQ</span><span class="sxs-lookup"><span data-stu-id="cd822-115">MSMQ</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/msmq.md)  
  
-   [<span data-ttu-id="cd822-116">COM +</span><span class="sxs-lookup"><span data-stu-id="cd822-116">COM+</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/com.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd822-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd822-117">See Also</span></span>  
 [<span data-ttu-id="cd822-118">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="cd822-118">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cd822-119">エンド ツー エンドのトレース</span><span class="sxs-lookup"><span data-stu-id="cd822-119">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
