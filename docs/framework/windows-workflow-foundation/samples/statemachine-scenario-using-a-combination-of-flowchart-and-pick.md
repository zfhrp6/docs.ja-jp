---
title: "FlowChart と Pick の組み合わせを使用する StateMachine シナリオ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# FlowChart と Pick の組み合わせを使用する StateMachine シナリオ
このサンプルでは、<xref:System.Activities.Statements.Flowchart> アクティビティと <xref:System.Activities.Statements.Pick> アクティビティを組み合わせて簡単なストップウォッチ シナリオを実装する方法を示します。このサンプルでは、Pick アクティビティ内で Receive と Send を使用して、ストップウォッチ イベントをリッスンします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## サンプルの詳細  
 次の表に、このサンプルのプロジェクトを示します。  
  
|||  
|-|-|  
|プロジェクト名|説明|  
|StopWatchService|このプロジェクトには、<xref:System.Activities.Statements.Flowchart> アクティビティと <xref:System.Activities.Statements.Pick> アクティビティを組み合わせて使用するストップウォッチ サンプルのステート マシンの実装が含まれます。<br /><br /> <xref:System.Activities.Statements.Pick> アクティビティには、`GetStart`、`GetStop`、および `GetOff` の各イベントをリッスンする 3 つの <xref:System.Activities.Statements.PickBranch> ステートメントが <xref:System.Activities.Statements.Pick.Branches%2A> プロパティ内にあります。受信イベントに基づいて、分岐のいずれかのトリガーがアクティブになり、対応する <xref:System.Activities.Statements.PickBranch.Action%2A> が起動されます。<xref:System.Activities.Statements.PickBranch.Action%2A> プロパティには、遷移が正当な遷移であるかどうかを評価する <xref:System.Activities.Statements.Switch%601> ステートメントがあります。正当な遷移の場合、`currentState` プロパティが遷移中の状態に更新され、クライアントに送信されます。<br /><br /> <xref:System.Activities.Statements.Flowchart> の最後にある <xref:System.Activities.Statements.FlowDecision> アクティビティは、`currentState` プロパティを評価して、終了状態であるかどうかを確認します。終了状態の場合、ワークフローは終了します。それ以外の場合は、<xref:System.Activities.Statements.Pick> アクティビティの先頭に戻ります。このアクティビティでは、ワークフローは他のストップウォッチ イベントを待機します。|  
|StopWatchClient|このプロジェクトは、簡単な Send アクティビティまたは Receive アクティビティを組み合わせてさまざまなストップウォッチ イベントを送信する簡単なシーケンシャル ワークフロー コンソール アプリケーションです。|  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、StateMachineWithPick.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] から StopWatchService.exe を管理者として開始します。これを行うには、.exe ファイルを右クリックし、**\[管理者として実行\]** をクリックします。  
  
    1.  StateMachineWithPick\\CS\\StopWatchService\\bin\\Debug フォルダーに移動します。  
  
    2.  StopWatchService.exe ファイルを右クリックし、**\[管理者として実行\]** をクリックします。  
  
4.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 内から StopWatchClient クライアント アプリケーションを開始します。  
  
    1.  **ソリューション エクスプローラー**で、**StopWatchClient** プロジェクトを右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
    2.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
5.  状態遷移を確認するには、StopWatchService.exe のコンソール ウィンドウに切り替えます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## 参照