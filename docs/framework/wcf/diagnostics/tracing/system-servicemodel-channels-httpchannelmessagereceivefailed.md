---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a258b315b5a8537de87a603b5d1ec0c18387ddbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="d9c5a-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="d9c5a-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="d9c5a-103">HTTP チャネルを介したメッセージの受信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d9c5a-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d9c5a-104">説明</span><span class="sxs-lookup"><span data-stu-id="d9c5a-104">Description</span></span>  
 <span data-ttu-id="d9c5a-105">このトレースは、警告またはエラーとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="d9c5a-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="d9c5a-106">どちらの場合であっても、このトレースは、受信 HTTP 要求に対して互換性のあるリスナーが見つからない場合に出力され、HTTP 要求は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="d9c5a-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="d9c5a-107">これは、要求の HTTP 動詞が HTTP リスナーによって認識されない、または要求が対象としているアドレスでリッスンしているリスナーがないために発生します。</span><span class="sxs-lookup"><span data-stu-id="d9c5a-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="d9c5a-108">このトレースは、自己ホスト型の場合は警告を出力し、サービスが IIS でホストされている場合はエラーを出力します。</span><span class="sxs-lookup"><span data-stu-id="d9c5a-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c5a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9c5a-109">See Also</span></span>  
 [<span data-ttu-id="d9c5a-110">トレース</span><span class="sxs-lookup"><span data-stu-id="d9c5a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d9c5a-111">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d9c5a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d9c5a-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="d9c5a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
