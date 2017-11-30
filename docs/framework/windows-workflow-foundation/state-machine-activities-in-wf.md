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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5056557c9fee74e9a16b235220c797e1f6356ce3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="14d01-102">WF のステート マシン アクティビティ</span><span class="sxs-lookup"><span data-stu-id="14d01-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="14d01-103"> には、ステート マシン ワーク フローを作成するための、システム指定のいくつかのアクティビティおよびアクティビティ デザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="14d01-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="14d01-104">使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="14d01-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="14d01-105">ステート マシンの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="14d01-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="14d01-106">ステート マシンの最終状態を表します。</span><span class="sxs-lookup"><span data-stu-id="14d01-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="14d01-107"><xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="14d01-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="14d01-108">詳細については、次を参照してください。 [FinalState アクティビティ デザイナー](/visualstudio/workflow-designer/finalstate-activity-designer)です。</span><span class="sxs-lookup"><span data-stu-id="14d01-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="14d01-109">2 つの状態間の遷移を表します。</span><span class="sxs-lookup"><span data-stu-id="14d01-109">Represents the transition between two states.</span></span> <span data-ttu-id="14d01-110">ない**ツールボックス**の項目<xref:System.Activities.Statements.Transition>; は、ドラッグして行を削除する 2 つの状態遷移をワークフロー デザイナーで作成するか、または別ときに表示される三角形で状態をドロップして 1 つの状態が置かれています。</span><span class="sxs-lookup"><span data-stu-id="14d01-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="14d01-111">詳細については、次を参照してください。 [Transition アクティビティ デザイナー](/visualstudio/workflow-designer/transition-activity-designer)です。</span><span class="sxs-lookup"><span data-stu-id="14d01-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14d01-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="14d01-112">See Also</span></span>  
 [<span data-ttu-id="14d01-113">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="14d01-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
