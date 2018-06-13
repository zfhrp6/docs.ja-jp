---
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 5a2f23a3335f938b26a378010e083525803ffb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33470492"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="f8214-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="f8214-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="f8214-103">Id: 138</span><span class="sxs-lookup"><span data-stu-id="f8214-103">Id: 138</span></span>  
  
 <span data-ttu-id="f8214-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="f8214-104">Severity: Error</span></span>  
  
 <span data-ttu-id="f8214-105">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="f8214-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="f8214-106">説明</span><span class="sxs-lookup"><span data-stu-id="f8214-106">Description</span></span>  
 <span data-ttu-id="f8214-107">このイベントは、参加要素の回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="f8214-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="f8214-108">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="f8214-108">Data loss may result from this error.</span></span> <span data-ttu-id="f8214-109">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8214-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8214-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8214-110">See Also</span></span>  
 [<span data-ttu-id="f8214-111">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="f8214-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="f8214-112">イベント一覧</span><span class="sxs-lookup"><span data-stu-id="f8214-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
