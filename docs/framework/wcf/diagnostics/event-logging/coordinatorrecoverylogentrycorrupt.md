---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3f51d1269f5ca89f4f02257c8accef3423aa7eb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472684"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="26e73-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="26e73-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="26e73-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="26e73-103">Id: 139</span></span>  
  
 <span data-ttu-id="26e73-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="26e73-104">Severity: Error</span></span>  
  
 <span data-ttu-id="26e73-105">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="26e73-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="26e73-106">説明</span><span class="sxs-lookup"><span data-stu-id="26e73-106">Description</span></span>  
 <span data-ttu-id="26e73-107">このイベントは、コーディネーターの回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="26e73-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="26e73-108">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="26e73-108">Data loss may result from this error.</span></span> <span data-ttu-id="26e73-109">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="26e73-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e73-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="26e73-110">See Also</span></span>  
 [<span data-ttu-id="26e73-111">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="26e73-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="26e73-112">イベント一覧</span><span class="sxs-lookup"><span data-stu-id="26e73-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
