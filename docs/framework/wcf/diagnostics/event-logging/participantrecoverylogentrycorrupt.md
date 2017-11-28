---
title: ParticipantRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 134cc6c1c3f0a04b55cc20aa7d9c7cadbe9c09af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="c2034-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="c2034-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="c2034-103">Id: 138</span><span class="sxs-lookup"><span data-stu-id="c2034-103">Id: 138</span></span>  
  
 <span data-ttu-id="c2034-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="c2034-104">Severity: Error</span></span>  
  
 <span data-ttu-id="c2034-105">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="c2034-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="c2034-106">説明</span><span class="sxs-lookup"><span data-stu-id="c2034-106">Description</span></span>  
 <span data-ttu-id="c2034-107">このイベントは、参加要素の回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="c2034-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="c2034-108">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="c2034-108">Data loss may result from this error.</span></span> <span data-ttu-id="c2034-109">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2034-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2034-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2034-110">See Also</span></span>  
 [<span data-ttu-id="c2034-111">イベントのログ記録</span><span class="sxs-lookup"><span data-stu-id="c2034-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="c2034-112">イベントの一般的なリファレンス</span><span class="sxs-lookup"><span data-stu-id="c2034-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
