---
title: インスタンスのアクティブ化処理
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: a1b78dc62fbdc6e5551addf400ceb14dc9e822f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516829"
---
# <a name="instance-activation"></a>インスタンスのアクティブ化処理
SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なワークフロー インスタンスを永続性データベースで検出します。 このタスクは、実行可能なワークフロー インスタンスを検出すると、このインスタンスをアクティブ化することができるワークフロー ホストに通知します。 Instance Store がアクティブ化可能なワークフロー インスタンスを検出した場合、ワークフロー ホストをアクティブ化する汎用ホストに Instance Store が通知を行い、ワークフロー ホストがワークフロー インスタンスを実行します。 このトピックの以降のセクションでは、インスタンスのアクティブ化処理を詳細に説明します。  
  
##  <a name="RunnableSection"></a> 検出と実行可能ワークフロー インスタンスをアクティブ化  
 SQL Workflow Instance Store がワークフロー インスタンスを考慮*runnable*インスタンスが中断状態または完了状態ではなくを次の条件を満たしている場合。  
  
-   インスタンスがロック解除されていて、保留タイマーの期限が切れている。  
  
-   インスタンスに期限切れのロックがある。  
  
-   インスタンスのロックが解除されていると、その状態が**Executing**です。  
  
 SQL Workflow Instance Store は、実行可能なインスタンスを見つけると <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> を生成します。 その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> に定期受信し、インスタンスの読み込みが可能なワークフロー ホストは、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> を実行してインスタンスをメモリに読み込みます。 ワークフロー ホストはホストとインスタンスは、メタデータのプロパティを持っている場合は、ワークフロー インスタンスを読み込むことができると見なされます**WorkflowServiceType**同じ値に設定します。  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>アクティブ化可能なワークフロー インスタンスの検出とアクティブ化  
 ワークフロー インスタンスと見なされます*アクティブ化可能な*インスタンスが実行可能な場合は、インスタンスを読み込むことができるワークフロー ホストが実行されていないコンピューターにします。 実行可能なワークフロー インスタンスの定義については、前の「実行可能なワークフロー インスタンスの検出とアクティブ化」を参照してください。  
  
 SQL Workflow Instance Store は、データベースでアクティブ化可能なワークフロー インスタンスを見つけると <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> を生成します。 その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> に定期受信している汎用ホストは、イベントを受け取ると、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> を実行して、ワークフロー ホストの作成に必要なアクティブ化のパラメーターを取得します。 汎用ホストは、このアクティブ化パラメーターを使用してワークフロー ホストを作成します。作成されたワークフロー ホストは、実行可能なサービス インスタンスを読み込んで実行します。  
  
## <a name="generic-hosts"></a>汎用ホスト  
 汎用ホストは、メタデータ プロパティの値を持つホスト**WorkflowServiceType**汎用ホスト用に設定されている**WorkflowServiceType.Any**ワークフロー型を処理できることを示すためにします。 汎用ホストは、という XName パラメーターを持つ**ActivationType**です。  
  
 現在、SQL Workflow Instance Store には、汎用ホストに設定、ActivationType パラメーターの値をサポートしています。 **WAS**です。 ActivationType が WAS に設定されていない場合、SQL Workflow Instance Store は <xref:System.Runtime.DurableInstancing.InstancePersistenceException> をスローします。 付属するワークフロー管理サービス、[!INCLUDE[dublin](../../../includes/dublin-md.md)]がライセンス認証の種類に設定された汎用ホストは、 **WAS**です。  
  
 WAS アクティブ化の場合、汎用ホストは、新しいホストをアクティブ化できるエンドポイント アドレスを派生する一連のアクティブ化パラメーターを要求します。 WAS アクティブ化のアクティブ化パラメーターは、サイトの名前、サイトを基準としたアプリケーションの相対パス、アプリケーションを基準としたサービスの相対パスです。 SQL Workflow Instance Store は、<xref:System.Activities.DurableInstancing.SaveWorkflowCommand> の実行中にこれらのアクティブ化パラメーターを格納します。  
  
## <a name="runnable-instances-detection-period"></a>実行可能インスタンス検出期間  
 **実行可能インスタンス検出期間**SQL Workflow Instance Store のプロパティを SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフローを検出する検出タスクを実行するまでの期間を指定します前回の検出サイクルの後に、永続性データベースでのインスタンス。 参照してください[実行可能インスタンス検出期間](../../../docs/framework/windows-workflow-foundation/runnable-instances-detection-period.md)このプロパティの詳細についてはします。
