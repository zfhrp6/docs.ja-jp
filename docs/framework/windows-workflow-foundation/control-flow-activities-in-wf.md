---
title: "WF 内の制御フロー アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e8520e34cf9bd9d31e9b877849e7c9611d6d989
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="control-flow-activities-in-wf"></a><span data-ttu-id="a63d0-102">WF 内の制御フロー アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a63d0-102">Control Flow Activities in WF</span></span>
<span data-ttu-id="a63d0-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、ワークフロー内の実行フローを制御するアクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="a63d0-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] provides several activities for controlling flow of execution within a workflow.</span></span> <span data-ttu-id="a63d0-104">このようなアクティビティの一部 (`Switch` や `If`) は、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)] など、プログラミング環境のアクティビティと似たフロー制御構造を実装しています。一方、その他は新しいプログラミング構造をモデル化しています (`Pick` など)。</span><span class="sxs-lookup"><span data-stu-id="a63d0-104">Some of these activities (such as `Switch` and `If`) implement flow control structures similar to those in programming environments such as [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], while others (such as `Pick`) model new programming structures.</span></span>  
  
 <span data-ttu-id="a63d0-105">`Parallel` や `ParallelForEach` などのアクティビティは、同時実行のために複数の子アクティビティをスケジュールできますが、シングル スレッドのみがワークフローに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a63d0-105">Note that while activities such as the `Parallel` and `ParallelForEach` activities schedule multiple child activities for execution simultaneously, only a single thread is used for a workflow.</span></span> <span data-ttu-id="a63d0-106">これらのアクティビティのそれぞれの子アクティビティは連続して実行され、連続するアクティビティは前のアクティビティが完了するかアイドルになるまで実行されません。</span><span class="sxs-lookup"><span data-stu-id="a63d0-106">Each child activity of these activities executes sequentially and successive activities do not execute until previous activities either complete or go idle.</span></span> <span data-ttu-id="a63d0-107">その結果、これらのアクティビティは、ブロック処理の可能性がある複数のアクティビティがインターリーブ形式で実行されるアプリケーションの場合に最も有効です。</span><span class="sxs-lookup"><span data-stu-id="a63d0-107">As a result, these activities are most useful for applications in which several potentially blocking activities must execute in an interleaved fashion.</span></span> <span data-ttu-id="a63d0-108">これらのアクティビティにアイドルになる子アクティビティがない場合、`Parallel` アクティビティは `Sequence` アクティビティとまったく同様に実行され、`ParallelForEach` アクティビティは `ForEach` アクティビティとまったく同様に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a63d0-108">If none of the child activities of these activities go idle, a `Parallel` activity executes just like a `Sequence` activity, and a `ParallelForEach` activity executes just like a `ForEach` activity.</span></span> <span data-ttu-id="a63d0-109">しかし、非同期アクティビティ (<xref:System.Activities.AsyncCodeActivity> から派生するアクティビティなど) またはメッセージング アクティビティが使用されると、子アクティビティがそのメッセージ受信を待っていても、または非同期作業を完了する必要があっても、コントロールは次の分岐にパスします。</span><span class="sxs-lookup"><span data-stu-id="a63d0-109">If, however, asynchronous activities (such as activities that derive from <xref:System.Activities.AsyncCodeActivity>) or messaging activities are used, control will pass to the next branch while the child activity waits for its message to be received or its asynchronous work to be completed.</span></span>  
  
## <a name="flow-control-activities"></a><span data-ttu-id="a63d0-110">フロー制御アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a63d0-110">Flow control activities</span></span>  
  
|<span data-ttu-id="a63d0-111">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a63d0-111">Activity</span></span>|<span data-ttu-id="a63d0-112">説明</span><span class="sxs-lookup"><span data-stu-id="a63d0-112">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|<span data-ttu-id="a63d0-113">含まれるアクティビティを 1 回実行し、条件が `true` の間はその実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-113">Executes the contained activities once and continues to do so while a condition is `true`.</span></span>|  
|<xref:System.Activities.Statements.ForEach%601>|<span data-ttu-id="a63d0-114">コレクション内の要素ごとに埋め込みステートメントを順番に実行します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-114">Executes an embedded statement in sequence for each element in a collection.</span></span> <span data-ttu-id="a63d0-115"><xref:System.Activities.Statements.ForEach%601> はキーワード `foreach` と似ていますが、言語ステートメントではなくアクティビティとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="a63d0-115"><xref:System.Activities.Statements.ForEach%601> is similar to the keyword `foreach`, but is implemented as an activity rather than a language statement.</span></span>|  
|<xref:System.Activities.Statements.If>|<span data-ttu-id="a63d0-116">条件が `true` の場合は含まれるアクティビティを実行します。条件が <xref:System.Activities.Statements.If.Else%2A> の場合は `false` プロパティに含まれるアクティビティを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a63d0-116">Executes contained activities if a condition is `true`, and can execute activities contained in the <xref:System.Activities.Statements.If.Else%2A> property if the condition is `false`.</span></span>|  
|<xref:System.Activities.Statements.Parallel>|<span data-ttu-id="a63d0-117">含まれるアクティビティを並列実行します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-117">Executes contained activities in parallel.</span></span>|  
|<xref:System.Activities.Statements.ParallelForEach%601>|<span data-ttu-id="a63d0-118">コレクション内の要素ごとに埋め込みステートメントを並行実行します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-118">Executes an embedded statement in parallel for each element in a collection.</span></span>|  
|<xref:System.Activities.Statements.Pick>|<span data-ttu-id="a63d0-119">イベント ベースの制御フロー モデリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-119">Provides event-based control flow modeling.</span></span>|  
|<xref:System.Activities.Statements.PickBranch>|<span data-ttu-id="a63d0-120"><xref:System.Activities.Statements.Pick> アクティビティ内の実行パスを表します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-120">Represents a potential path of execution in a <xref:System.Activities.Statements.Pick> activity.</span></span>|  
|<xref:System.Activities.Statements.Sequence>|<span data-ttu-id="a63d0-121">含まれるアクティビティを連続実行します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-121">Executes contained activities in sequence.</span></span>|  
|<xref:System.Activities.Statements.Switch%601>|<span data-ttu-id="a63d0-122">指定された式の値に基づいて、実行する複数のアクティビティから 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-122">Selects one choice from a number of activities to execute, based on the value of a given expression.</span></span>|  
|<xref:System.Activities.Statements.While>|<span data-ttu-id="a63d0-123">条件が `true` である間は、含まれるアクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="a63d0-123">Executes contained activities while a condition is `true`.</span></span>|
