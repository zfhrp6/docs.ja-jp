---
title: MessageQueueDuplicatedSocketLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e1356c1b6146d2c54f81a8f4221579490068f5c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="c4c69-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="c4c69-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="c4c69-103">Id: 165</span><span class="sxs-lookup"><span data-stu-id="c4c69-103">Id: 165</span></span>  
  
 <span data-ttu-id="c4c69-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="c4c69-104">Severity: Error</span></span>  
  
 <span data-ttu-id="c4c69-105">カテゴリ: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="c4c69-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="c4c69-106">説明</span><span class="sxs-lookup"><span data-stu-id="c4c69-106">Description</span></span>  
 <span data-ttu-id="c4c69-107">このイベントは、複製されたソケットのディスパッチ中にエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c4c69-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="c4c69-108">このハンドルは現在プロセスでリークされています。</span><span class="sxs-lookup"><span data-stu-id="c4c69-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="c4c69-109">イベントには、ソース、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4c69-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c69-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4c69-110">See Also</span></span>  
 [<span data-ttu-id="c4c69-111">イベントのログ記録</span><span class="sxs-lookup"><span data-stu-id="c4c69-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="c4c69-112">イベントの一般的なリファレンス</span><span class="sxs-lookup"><span data-stu-id="c4c69-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
