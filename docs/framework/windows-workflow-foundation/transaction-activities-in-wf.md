---
title: "WF におけるトランザクションのアクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# WF におけるトランザクションのアクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、トランザクションや、補正、取り消しをモデル化するためのシステム指定のアクティビティがいくつかあります。これらのプログラミング モデルにより、ビジネス ロジックとエラー処理の変更の場合に、ワークフローは進行を続けることができます。トランザクション、補正および取り消し[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[トランザクション](../../../docs/framework/windows-workflow-foundation//workflow-transactions.md)」、「[補正](../../../docs/framework/windows-workflow-foundation//compensation.md)」および「[取り消し](../../../docs/framework/windows-workflow-foundation//modeling-cancellation-behavior-in-workflows.md)」を参照してください。  
  
## トランザクションのアクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|アクティビティの形式のキャンセル ロジックを、アクティビティとしても表される実行のメイン パスに関連付けます。|  
|<xref:System.Activities.Statements.CompensableActivity>|子アクティビティの補正をサポートします。|  
|<xref:System.Activities.Statements.Compensate>|<xref:System.Activities.Statements.CompensableActivity> の補正ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.Confirm>|<xref:System.Activities.Statements.CompensableActivity> の確認ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.TransactionScope>|トランザクションの境界を設定します。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|受信したメッセージによって開始されるトランザクションの有効期間を制御します。トランザクションは、開始メッセージでワークフローにフローすることも、メッセージの受信時にディスパッチャーが作成することも可能です。 **Note:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> は、**ツールボックス** の **\[メッセージング\]** セクションにあります。|