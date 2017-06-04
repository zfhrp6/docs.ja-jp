---
title: "トレースを使用したワークフロー実行時間の決定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# トレースを使用したワークフロー実行時間の決定
このトピックでは、ワークフロー トレースを使用して、正常に完了した自己ホスト型ワークフローの実行所要時間を決定する方法を示します。  
  
### ワークフロー トレースを使用してワークフロー アプリケーションの実行時間を決定するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を起動します。**\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。**\[C\#\]** から **\[ワークフロー\]** ノードを選択します。テンプレートの一覧から **\[ワークフロー コンソール アプリケーション\]** を選択します。新しいプロジェクトに `WorkflowDurationTracing` という名前を設定し、**\[OK\]** をクリックします。  
  
2.  Workflow1.xaml を開きます。<xref:System.Activities.Statements.Delay> アクティビティをデザイナー画面にドラッグします。00:00:10 \(10 秒\) という値をアクティビティの "実行時間" プロパティに割り当てます。  
  
3.  **\[スタート\]** ボタン、**\[ファイル名を指定して実行\]** の順にクリックし、「`eventvwr.exe`」と入力してイベント ビューアーを開きます。  
  
4.  ワークフロー トレースを有効にしていない場合は、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]**、**\[アプリケーション サーバー \- アプリケーション\]** の順に展開します。**\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。**\[デバッグ\]** を右クリックし、**\[ログを有効にする\]** をクリックします。ワークフローが実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
5.  Ctrl \+ Shift \+ B キーを押してワークフロー アプリケーションを実行します。  
  
6.  イベント ビューアーで、1009 の ID を持つ最近のイベント、および次のようなメッセージを探します。メッセージがログに記録された時刻を書き留めます。  
  
 **Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**  
  
7.  さらに、1001 の ID を持つ最近のイベント、および次のようなメッセージを探します。このメッセージのログに記録された値から前のメッセージの時刻を差し引いてワークフロー実行時間を決定します。この時間は約 10 秒になります。  
  
 **WorkflowInstance Id: '1bbac57b\-3322\-498e\-9e27\-8833fda3a5bf' has completed in the Closed state.**  
  
## 参照  
 [ワークフロー トレース](../../../docs/framework/windows-workflow-foundation//workflow-tracing.md)   
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [App Fabric を使用したアプリケーションの監視](http://go.microsoft.com/fwlink/?LinkId=201275)