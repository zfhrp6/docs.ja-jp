---
title: CoordinatorRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1db6f8dc4136623f35767c122dbea46fd4706b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="3e60a-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="3e60a-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="3e60a-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="3e60a-103">Id: 139</span></span>  
  
 <span data-ttu-id="3e60a-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="3e60a-104">Severity: Error</span></span>  
  
 <span data-ttu-id="3e60a-105">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="3e60a-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="3e60a-106">説明</span><span class="sxs-lookup"><span data-stu-id="3e60a-106">Description</span></span>  
 <span data-ttu-id="3e60a-107">このイベントは、コーディネーターの回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="3e60a-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="3e60a-108">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="3e60a-108">Data loss may result from this error.</span></span> <span data-ttu-id="3e60a-109">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e60a-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e60a-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e60a-110">See Also</span></span>  
 [<span data-ttu-id="3e60a-111">イベントのログ記録</span><span class="sxs-lookup"><span data-stu-id="3e60a-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="3e60a-112">イベントの一般的なリファレンス</span><span class="sxs-lookup"><span data-stu-id="3e60a-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
