---
title: "ホストのロック更新時間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48a5d2e1d8c5381f322ea1b6ffc9022853683efc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="host-lock-renewal-period"></a><span data-ttu-id="f5a28-102">ホストのロック更新時間</span><span class="sxs-lookup"><span data-stu-id="f5a28-102">Host Lock Renewal Period</span></span>
<span data-ttu-id="f5a28-103">**ホストのロック更新時間**SQL Workflow Instance Store のプロパティを使用して、ホストがワークフロー インスタンスに対してロックを更新するまでの時間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f5a28-103">The **Host Lock Renewal Period** property of the SQL Workflow Instance Store lets you specify the time period within which the host renews its lock on a workflow instance.</span></span> <span data-ttu-id="f5a28-104">ロックは、ホストのロック更新時間 + 30 秒の間は有効です。</span><span class="sxs-lookup"><span data-stu-id="f5a28-104">The lock remains valid for Host Lock Renewal Period + 30 seconds.</span></span> <span data-ttu-id="f5a28-105">この期間内にホストがロックの更新 (つまり、リースを延長) に失敗した場合は、ロックの有効期限が切れ、永続化プロバイダーはインスタンスのロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="f5a28-105">If the host fails to renew the lock (in other words, extend the lease) within this time period, the lock expires and the persistence provider unlocks the instance.</span></span> <span data-ttu-id="f5a28-106">このプロパティの値は"hh:mm:ss"の形式は TimeSpan 型です。</span><span class="sxs-lookup"><span data-stu-id="f5a28-106">The value for this property is of type TimeSpan of the form "hh:mm:ss".</span></span> <span data-ttu-id="f5a28-107">最小許容値は"00: 00:01"(1 秒)。</span><span class="sxs-lookup"><span data-stu-id="f5a28-107">The minimum permitted value is "00:00:01" (1 second).</span></span> <span data-ttu-id="f5a28-108">このプロパティの既定値は"00: 00:30"(30 秒)。</span><span class="sxs-lookup"><span data-stu-id="f5a28-108">The default value of this property is "00:00:30" (30 seconds).</span></span>  
  
 <span data-ttu-id="f5a28-109">このプロパティは、所有するワークフロー サービス インスタンスのロックを解除する前にワークフロー サービス ホストがエラーになった場合に重要です。</span><span class="sxs-lookup"><span data-stu-id="f5a28-109">This property is significant in scenarios where a workflow service host fails before it can unlock a workflow service instance that it owns.</span></span> <span data-ttu-id="f5a28-110">このような場合、ロックの有効期限が切れた後に永続プロバイダーによって永続性データベースのワークフロー サービス インスタンスのロックが削除され、サーバー ファーム内の同じコンピューターまたは別のコンピューターで実行されている別のワークフロー サービスホストがロックを取得してメモリにワークフロー サービス インスタンスを読み込み、最後の永続化状態から実行を再開できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f5a28-110">In this scenario, the lock on the workflow service instance in the persistence database is removed by the persistence provider after the lock expires so that another workflow service host running on the same computer or another computer in a server farm can acquire the lock and load the workflow service instance into memory to resume its execution from its last persisted state.</span></span>  
  
 <span data-ttu-id="f5a28-111">このプロパティに大きな値を設定すると、ワークフロー サービス インスタンスが永続性データベースで長時間ロックされ、最後の永続性ポイントからインスタンスが回復するのが遅くなります。</span><span class="sxs-lookup"><span data-stu-id="f5a28-111">Setting a higher value for this property causes the workflow service instances to be locked in the persistence database for a longer time and therefore delays the recovery of the instance from the last persistence point.</span></span> <span data-ttu-id="f5a28-112">このプロパティに短い間隔を設定すると、ワークフロー サービス ホストの新しいインスタンスがすぐにエラーになったワークフロー サービス インスタンスを取得することになりますが、これによってワークフロー サービス ホストと SQL Server データベースの負荷が増加します。</span><span class="sxs-lookup"><span data-stu-id="f5a28-112">Setting a short interval for this property causes the new instance of the workflow service host to pick up the failed workflow service instance quickly, but causes an increase in workload for the workflow service host and the SQL Server database.</span></span>  
  
 <span data-ttu-id="f5a28-113">SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、有効期限切れのロックを持つインスタンスを検出します。</span><span class="sxs-lookup"><span data-stu-id="f5a28-113">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects instances with expired locks on them.</span></span> <span data-ttu-id="f5a28-114">有効期限切れのロックを持つインスタンスが見つかると、そのインスタンスを RunnableInstances テーブルに置き、ワークフロー ホストがそのインスタンスを取得して実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f5a28-114">When it finds instances with expired locks, it places the instances in the RunnableInstances table so that a workflow host can pick up and run these instances.</span></span>
