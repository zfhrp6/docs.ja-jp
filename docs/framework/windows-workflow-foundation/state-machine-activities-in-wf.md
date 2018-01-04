---
title: "WF のステート マシン アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62a211b51f37b306ffcc6b3b9a1ac65ccadd9db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="3eede-102">WF のステート マシン アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3eede-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="3eede-103"> には、ステート マシン ワーク フローを作成するための、システム指定のいくつかのアクティビティおよびアクティビティ デザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3eede-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="3eede-104">使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="3eede-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="3eede-105">ステート マシンの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="3eede-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="3eede-106">ステート マシンの最終状態を表します。</span><span class="sxs-lookup"><span data-stu-id="3eede-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="3eede-107"><xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="3eede-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="3eede-108">詳細については、次を参照してください。 [FinalState アクティビティ デザイナー](/visualstudio/workflow-designer/finalstate-activity-designer)です。</span><span class="sxs-lookup"><span data-stu-id="3eede-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="3eede-109">2 つの状態間の遷移を表します。</span><span class="sxs-lookup"><span data-stu-id="3eede-109">Represents the transition between two states.</span></span> <span data-ttu-id="3eede-110">ない**ツールボックス**の項目<xref:System.Activities.Statements.Transition>; は、ドラッグして行を削除する 2 つの状態遷移をワークフロー デザイナーで作成するか、または別ときに表示される三角形で状態をドロップして 1 つの状態が置かれています.</span><span class="sxs-lookup"><span data-stu-id="3eede-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="3eede-111">詳細については、次を参照してください。 [Transition アクティビティ デザイナー](/visualstudio/workflow-designer/transition-activity-designer)です。</span><span class="sxs-lookup"><span data-stu-id="3eede-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3eede-112">参照</span><span class="sxs-lookup"><span data-stu-id="3eede-112">See Also</span></span>  
 [<span data-ttu-id="3eede-113">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="3eede-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
