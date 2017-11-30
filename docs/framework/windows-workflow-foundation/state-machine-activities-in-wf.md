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
# <a name="state-machine-activities-in-wf"></a>WF のステート マシン アクティビティ
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には、ステート マシン ワーク フローを作成するための、システム指定のいくつかのアクティビティおよびアクティビティ デザイナーが用意されています。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。|  
|<xref:System.Activities.Statements.State>|ステート マシンの状態を表します。|  
|<xref:System.Activities.Core.Presentation.FinalState>|ステート マシンの最終状態を表します。 <xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。 詳細については、次を参照してください。 [FinalState アクティビティ デザイナー](/visualstudio/workflow-designer/finalstate-activity-designer)です。|  
|<xref:System.Activities.Statements.Transition>|2 つの状態間の遷移を表します。 ない**ツールボックス**の項目<xref:System.Activities.Statements.Transition>; は、ドラッグして行を削除する 2 つの状態遷移をワークフロー デザイナーで作成するか、または別ときに表示される三角形で状態をドロップして 1 つの状態が置かれています。 詳細については、次を参照してください。 [Transition アクティビティ デザイナー](/visualstudio/workflow-designer/transition-activity-designer)です。|  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
