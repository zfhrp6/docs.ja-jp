---
title: "インスタンスのアクティブ化処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# インスタンスのアクティブ化処理
SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なワークフロー インスタンスを永続性データベースで検出します。このタスクは、実行可能なワークフロー インスタンスを検出すると、このインスタンスをアクティブ化することができるワークフロー ホストに通知します。Instance Store がアクティブ化可能なワークフロー インスタンスを検出した場合、ワークフロー ホストをアクティブ化する汎用ホストに Instance Store が通知を行い、ワークフロー ホストがワークフロー インスタンスを実行します。このトピックの以降のセクションでは、インスタンスのアクティブ化処理を詳細に説明します。  
  
##  <a name="RunnableSection"></a> 実行可能なワークフロー インスタンスの検出とアクティブ化  
 SQL Workflow Instance Store がワークフロー インスタンスを*実行可能*と見なすのは、インスタンスが非中断状態または完了状態であり、次の条件を満たす場合です。  
  
-   インスタンスがロック解除されていて、保留タイマーの期限が切れている。  
  
-   インスタンスに期限切れのロックがある。  
  
-   インスタンスがロック解除されていて、ステータスが **Executing** である。  
  
 SQL Workflow Instance Store は、実行可能なインスタンスを見つけると <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> を生成します。その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> に定期受信し、インスタンスの読み込みが可能なワークフロー ホストは、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> を実行してインスタンスをメモリに読み込みます。ワークフロー ホストがワークフロー インスタンスを読み込みできると見なされるのは、ホストとインスタンスのメタデータ プロパティ **WorkflowServiceType** が同じ値に設定されている場合です。  
  
## アクティブ化可能なワークフロー インスタンスの検出とアクティブ化  
 ワークフロー インスタンスが*アクティブ化可能*と見なされるのは、そのインスタンスが実行可能であり、そのインスタンスを読み込むことが可能なワークフロー ホストがコンピューターで実行されていない場合です。実行可能なワークフロー インスタンスの定義については、前の「実行可能なワークフロー インスタンスの検出とアクティブ化」を参照してください。  
  
 SQL Workflow Instance Store は、データベースでアクティブ化可能なワークフロー インスタンスを見つけると <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> を生成します。その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> に定期受信している汎用ホストは、イベントを受け取ると、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> を実行して、ワークフロー ホストの作成に必要なアクティブ化のパラメーターを取得します。汎用ホストは、このアクティブ化パラメーターを使用してワークフロー ホストを作成します。作成されたワークフロー ホストは、実行可能なサービス インスタンスを読み込んで実行します。  
  
## 汎用ホスト  
 汎用ホストとは、汎用ホストのメタデータ プロパティ **WorkflowServiceType** が、任意のワークフロー型を処理できることを示す **WorkflowServiceType.Any** に設定されているホストです。汎用ホストには、**ActivationType** という XName パラメーターがあります。  
  
 現時点では、SQL Workflow Instance Store は、ActivationType パラメーターが **WAS** に設定された汎用ホストをサポートしています。ActivationType が WAS に設定されていない場合、SQL Workflow Instance Store は <xref:System.Runtime.DurableInstancing.InstancePersistenceException> をスローします。[!INCLUDE[dublin](../../../includes/dublin-md.md)] に付属するワークフロー管理サービスは、アクティブ化のタイプが **WAS** に設定された汎用ホストです。  
  
 WAS アクティブ化の場合、汎用ホストは、新しいホストをアクティブ化できるエンドポイント アドレスを派生する一連のアクティブ化パラメーターを要求します。WAS アクティブ化のアクティブ化パラメーターは、サイトの名前、サイトを基準としたアプリケーションの相対パス、アプリケーションを基準としたサービスの相対パスです。SQL Workflow Instance Store は、<xref:System.Activities.DurableInstancing.SaveWorkflowCommand> の実行中にこれらのアクティブ化パラメーターを格納します。  
  
## 実行可能インスタンス検出期間  
 SQL Workflow Instance Store の**実行可能インスタンス検出期間**プロパティは、前の検出サイクルの後、SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフロー インスタンスを永続性データベースで検出するために検出タスクを実行するまでの期間を指定します。このプロパティの詳細については、「[実行可能インスタンス検出期間](../../../docs/framework/windows-workflow-foundation//runnable-instances-detection-period.md)」を参照してください。