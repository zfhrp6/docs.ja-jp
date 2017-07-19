---
title: "WF のステート マシン アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# WF のステート マシン アクティビティ
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は、ステート マシン ワーク フローを作成するために、システム指定のいくつかのアクティビティおよびアクティビティ デザイナーを提供します。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。|  
|<xref:System.Activities.Statements.State>|ステート マシンの状態を表します。|  
|<xref:System.Activities.Core.Presentation.FinalState>|ステート マシンの最終状態を表します。<xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。詳細については、「[FinalState アクティビティ デザイナー](../Topic/FinalState%20Activity%20Designer.md)」を参照してください。|  
|<xref:System.Activities.Statements.Transition>|2 つの状態間の遷移を表します。<xref:System.Activities.Statements.Transition> の**ツールボックス** の項目はありません。移行は、ワーク フロー デザイナーで、2 つの状態の間で行をドラッグ アンド ドロップするか、または 1 つの状態を別の状態の上に配置したときに表示される三角形の上に状態をドロップして作成されます。詳細については、「[Transition アクティビティ デザイナー](../Topic/Transition%20Activity%20Designer.md)」を参照してください。|  
  
## 参照  
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)