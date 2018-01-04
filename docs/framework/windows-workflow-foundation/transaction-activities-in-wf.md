---
title: "WF におけるトランザクションのアクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b12cfa1cecde648e66872784eb1e353f8c16da8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-activities-in-wf"></a>WF におけるトランザクションのアクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、トランザクションや、補正、取り消しをモデル化するためのシステム指定のアクティビティがいくつかあります。 これらのプログラミング モデルにより、ビジネス ロジックとエラー処理の変更の場合に、ワークフローは進行を続けることができます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]トランザクションや、補正、取り消しを参照してください。[トランザクション](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)、[補正](../../../docs/framework/windows-workflow-foundation/compensation.md)、および[キャンセル](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)です。  
  
## <a name="transaction-activities"></a>トランザクションのアクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|アクティビティの形式のキャンセル ロジックを、アクティビティとしても表される実行のメイン パスに関連付けます。|  
|<xref:System.Activities.Statements.CompensableActivity>|子アクティビティの補正をサポートします。|  
|<xref:System.Activities.Statements.Compensate>|<xref:System.Activities.Statements.CompensableActivity> の補正ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.Confirm>|<xref:System.Activities.Statements.CompensableActivity> の確認ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.TransactionScope>|トランザクションの境界を設定します。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|受信したメッセージによって開始されるトランザクションの有効期間のスコープを設定します。 トランザクションは、開始メッセージでワークフローにフローすることも、メッセージの受信時にディスパッチャーが作成することも可能です。 **注:** 、<xref:System.ServiceModel.Activities.TransactedReceiveScope>内にある、**メッセージング**のセクションで、**ツールボックス**です。|
