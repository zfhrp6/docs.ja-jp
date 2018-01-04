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
ms.workload: dotnet
ms.openlocfilehash: 3ea58a826920d440ab903270f796a3d94d17ad47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="85224-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="85224-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="85224-103">Id: 165</span><span class="sxs-lookup"><span data-stu-id="85224-103">Id: 165</span></span>  
  
 <span data-ttu-id="85224-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="85224-104">Severity: Error</span></span>  
  
 <span data-ttu-id="85224-105">カテゴリ: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="85224-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="85224-106">説明</span><span class="sxs-lookup"><span data-stu-id="85224-106">Description</span></span>  
 <span data-ttu-id="85224-107">このイベントは、複製されたソケットのディスパッチ中にエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="85224-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="85224-108">このハンドルは現在プロセスでリークされています。</span><span class="sxs-lookup"><span data-stu-id="85224-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="85224-109">イベントには、ソース、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="85224-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85224-110">参照</span><span class="sxs-lookup"><span data-stu-id="85224-110">See Also</span></span>  
 [<span data-ttu-id="85224-111">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="85224-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="85224-112">イベント一覧</span><span class="sxs-lookup"><span data-stu-id="85224-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
