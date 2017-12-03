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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd9dce1745c1a110ac2cbadd497c02c1323a2338
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="f9687-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="f9687-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="f9687-103">Id: 138</span><span class="sxs-lookup"><span data-stu-id="f9687-103">Id: 138</span></span>  
  
 <span data-ttu-id="f9687-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="f9687-104">Severity: Error</span></span>  
  
 <span data-ttu-id="f9687-105">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="f9687-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="f9687-106">説明</span><span class="sxs-lookup"><span data-stu-id="f9687-106">Description</span></span>  
 <span data-ttu-id="f9687-107">このイベントは、参加要素の回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="f9687-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="f9687-108">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="f9687-108">Data loss may result from this error.</span></span> <span data-ttu-id="f9687-109">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9687-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9687-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9687-110">See Also</span></span>  
 [<span data-ttu-id="f9687-111">イベントのログ記録</span><span class="sxs-lookup"><span data-stu-id="f9687-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="f9687-112">イベントの一般的なリファレンス</span><span class="sxs-lookup"><span data-stu-id="f9687-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
