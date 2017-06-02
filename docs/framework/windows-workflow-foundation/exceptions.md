---
title: "例外 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# 例外
ワークフローは、<xref:System.Activities.Statements.TryCatch> アクティビティを使用して、ワークフローの実行中に発生した例外を処理することができます。これらの例外は、処理することも可能ですが、<xref:System.Activities.Statements.Rethrow> アクティビティを使用して再スローすることもできます。<xref:System.Activities.Statements.TryCatch.Finally%2A> セクションのアクティビティは、<xref:System.Activities.Statements.TryCatch.Try%2A> セクションまたは <xref:System.Activities.Statements.TryCatch.Catches%2A> セクションが完了したときに実行されます。また、<xref:System.Activities.WorkflowApplication> インスタンスによってホストされるワークフローは <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> イベント ハンドラーを使用して、<xref:System.Activities.Statements.TryCatch> アクティビティで処理されない例外を処理することができます。  
  
## 例外の原因  
 ワークフローでは、例外は、次の方法で生成されます。  
  
-   <xref:System.Activities.Statements.TransactionScope> でのトランザクションのタイムアウト  
  
-   <xref:System.Activities.Statements.Throw> アクティビティを使用してワークフローからスローされた明示的な例外  
  
-   アクティビティからスローされた [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 例外  
  
-   ワークフローで使用されているライブラリ、コンポーネント、サービスなどの外部コードからスローされた例外  
  
## 例外処理  
 アクティビティからスローされた例外が処理されない場合、既定の動作では、ワークフロー インスタンスが終了します。カスタムの <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ハンドラーが存在する場合、このハンドラーで既定の動作をオーバーライドできます。このハンドラーがあると、ワークフロー ホストの作成者は、カスタムのログ記録、ワークフローの中止、ワークフローのキャンセル、ワークフローの終了などの適切な処理を実行できます。ワークフローが処理されない例外を発生する場合、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ハンドラーが呼び出されます。<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> から戻された3 つの可能なアクションがあり、これによりワークフローの最終結果が決定されます。  
  
-   **キャンセル** \- キャンセルされたワークフロー インスタンスは分岐実行の通常終了です。キャンセルの動作をモデル化できます \(たとえば、CancellationScope アクティビティを使用して\)。完了済みハンドラーはキャンセル プロセスが完了したときに呼び出されます。取り消されたワーク フローは キャンセル状態にあります。  
  
-   **終了** \- 終了したワークフロー インスタンスは再開または再起動できません。これにより完了イベントがトリガーされ、中断されたという理由の例外を提供できます。終了したハンドラーはキャンセル プロセスが終了したときに呼び出されます。終了したワークフローは失敗状態です。  
  
-   **中止** \- 永続的な構成した場合にのみ、中止されたワークフロー インスタンスを再開できます。永続化がない場合、ワークフローは再開できません。ワークフローが中止したポイントで、最後の永続性ポイントが失われるため \(メモリ内で\)、どの作業も終了します 。中止されたワーク フローに対して、中止プロセスが完了したときの例外を使用して、中止されたハンドラーが呼び出されます。しかし、キャンセルおよび終了と異なり、完了ハンドラーは呼び出されません。中止されたワーク フローが中断状態にあります。  
  
 次の例では、例外をスローするワークフローを呼び出しています。ワークフローで例外が処理されないため、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ハンドラーが呼び出されます。例外に関する情報を提供するために <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> が調査され、ワークフローは終了します。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### TryCatch アクティビティでの例外処理  
 ワークフロー内部での例外処理は、<xref:System.Activities.Statements.TryCatch> アクティビティで実行されます。<xref:System.Activities.Statements.TryCatch> アクティビティには、それぞれが特定の <xref:System.Exception> 型に関連付けられている <xref:System.Activities.Statements.Catch> アクティビティの <xref:System.Activities.Statements.TryCatch.Catches%2A> コレクションがあります。<xref:System.Activities.Statements.TryCatch> アクティビティの <xref:System.Activities.Statements.TryCatch.Try%2A> セクションに含まれているアクティビティからスローされた例外が、<xref:System.Activities.Statements.TryCatch.Catches%2A> コレクションの <xref:System.Activities.Statements.Catch%601> アクティビティの例外に一致する場合、スローされた例外が処理されます。例外が明示的に再スローされるか、新しい例外がスローされた場合、この例外は親アクティビティに渡されます。次のコード例は、<xref:System.Activities.Statements.TryCatch.Try%2A> セクションで <xref:System.Activities.Statements.Throw> アクティビティからスローされた <xref:System.ApplicationException> を処理する <xref:System.Activities.Statements.TryCatch> アクティビティを示しています。例外のメッセージが <xref:System.Activities.Statements.Catch%601> アクティビティによってコンソールに書き込まれた後、<xref:System.Activities.Statements.TryCatch.Finally%2A> セクションでメッセージがコンソールに書き込まれます。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 <xref:System.Activities.Statements.TryCatch.Finally%2A> セクションのアクティビティは、<xref:System.Activities.Statements.TryCatch.Try%2A> セクションまたは <xref:System.Activities.Statements.TryCatch.Catches%2A> セクションが正常に完了したときに実行されます。例外がスローされない場合 <xref:System.Activities.Statements.TryCatch.Try%2A> セクションは正常に終了し、例外がスローされるまたは再スローされない場合 <xref:System.Activities.Statements.TryCatch.Catches%2A> セクションは正常に完了します。例外が <xref:System.Activities.Statements.TryCatch> の <xref:System.Activities.Statements.TryCatch.Try%2A> セクションでスローされ、<xref:System.Activities.Statements.TryCatch.Catches%2A> セクションの <xref:System.Activities.Statements.Catch%601> で処理されないか、または <xref:System.Activities.Statements.TryCatch.Catches%2A> からスローされる場合、<xref:System.Activities.Statements.TryCatch.Finally%2A> のアクティビティは以下のいずれかが発生しない限り実行されます。  
  
-   高レベルの <xref:System.Activities.Statements.TryCatch> から再スローされるかにかかわらず、例外がワーク フローの高レベルの <xref:System.Activities.Statements.TryCatch> アクティビティによって取得されます。  
  
-   例外は高レベルの <xref:System.Activities.Statements.TryCatch>では扱われず、ワークフローのルートをエスケープし、ワーク フローが完了または中止ではなく取り消すように構成されます。<xref:System.Activities.WorkflowApplication> を使用してホストされたワークフローは、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> を処理し <xref:System.Activities.UnhandledExceptionAction> を返してこれを構成できます。<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> を処理する例は、このトピックですでに提供されています。ワークフロー サービスは <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> を使用し <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> を指定してこれを構成できます。<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> の構成の例は、[ワークフロー サービス ホストの拡張機能](../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md) を参照してください。  
  
## 例外処理と補正の比較  
 例外処理は、アクティビティの実行中に発生するという点で補正と異なります。補正が発生するのは、アクティビティが正常に完了した後です。例外処理では、アクティビティが例外を生成した後でクリーン アップを実行できます。また、補正処理では、前に完了したアクティビティの正常に完了した作業を元に戻すことが可能です。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][補正](../../../docs/framework/windows-workflow-foundation//compensation.md).  
  
## 参照  
 <xref:System.Activities.Statements.TryCatch>   
 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>   
 <xref:System.Activities.Statements.CompensableActivity>