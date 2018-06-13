---
title: WF におけるトランザクションのアクティビティ
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f2709601fc4fd88a1c5223a5a3e97e139ceca954
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516610"
---
# <a name="transaction-activities-in-wf"></a>WF におけるトランザクションのアクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、トランザクションや、補正、取り消しをモデル化するためのシステム指定のアクティビティがいくつかあります。 これらのプログラミング モデルにより、ビジネス ロジックとエラー処理の変更の場合に、ワークフローは進行を続けることができます。 トランザクションや、補正、取り消しの詳細については、次を参照してください。[トランザクション](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)、[補正](../../../docs/framework/windows-workflow-foundation/compensation.md)、および[キャンセル](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)です。  
  
## <a name="transaction-activities"></a>トランザクションのアクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|アクティビティの形式のキャンセル ロジックを、アクティビティとしても表される実行のメイン パスに関連付けます。|  
|<xref:System.Activities.Statements.CompensableActivity>|子アクティビティの補正をサポートします。|  
|<xref:System.Activities.Statements.Compensate>|<xref:System.Activities.Statements.CompensableActivity> の補正ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.Confirm>|<xref:System.Activities.Statements.CompensableActivity> の確認ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.TransactionScope>|トランザクションの境界を設定します。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|受信したメッセージによって開始されるトランザクションの有効期間のスコープを設定します。 トランザクションは、開始メッセージでワークフローにフローすることも、メッセージの受信時にディスパッチャーが作成することも可能です。 **注:** 、<xref:System.ServiceModel.Activities.TransactedReceiveScope>内にある、**メッセージング**のセクションで、**ツールボックス**です。|
