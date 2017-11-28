---
title: "簡単なポリシー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c704a9f3f27d63fb1a28db61f03cdc9b8de4370
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="simple-policy"></a>簡単なポリシー
このサンプルでは、ワークフロー内で <xref:System.Workflow.Activities.PolicyActivity> アクティビティを使用する方法を示します。  
  
 このサンプルのシーケンシャル ワークフローは、<xref:System.Workflow.Activities.PolicyActivity> アクティビティを使用して作成します。 ワークフローは、製品割引ワークフローを定義するために使用するフィールド `orderValue`、`customerType`、および `discount` を定義します。 ルール ファイルに定義済みのルールは、`orderValue` と `customerType` に基づいて、割引金額を設定します。 `orderValue` と `customerType` が `SimplePolicyWorkflow` クラス定義で設定されています。これを変更すると、動作を変更できます。 結果として得られた割引率は、<xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> クラスに定義されているイベント ハンドラ `SimplePolicyWorkflow` でコンソールに出力されます。  
  
### <a name="to-build-the-sample"></a>サンプルをビルドするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。  
  
### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
-   [SDK コマンド プロンプト] ウィンドウで、SimplePolicy\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は SimplePolicy\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [高度なポリシー](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
