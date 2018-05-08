---
title: トレースを使用したワークフロー実行時間の決定
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: 9f9c65f2c873d54da443db14e7f5797ef1e14174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>トレースを使用したワークフロー実行時間の決定
このトピックでは、ワークフロー トレースを使用して、正常に完了した自己ホスト型ワークフローの実行所要時間を決定する方法を示します。  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>ワークフロー トレースを使用してワークフロー アプリケーションの実行時間を決定するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。  選択**ファイル**、**新しい**、**プロジェクト**です。  **C#**、select、**ワークフロー**ノード。  選択**ワークフロー コンソール アプリケーション**テンプレートの一覧からです。  新しいプロジェクトの名前`WorkflowDurationTracing` をクリック**OK**です。  
  
2.  Workflow1.xaml を開きます。  <xref:System.Activities.Statements.Delay> アクティビティをデザイナー画面にドラッグします。 00:00:10 (10 秒) という値をアクティビティの "実行時間" プロパティに割り当てます。  
  
3.  クリックしてイベント ビューアーを開いて**開始**、**実行**、」と入力して`eventvwr.exe`です。  
  
4.  ワークフロー トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**. 選択**ビュー**、 **分析およびデバッグ ログ**です。 右クリック**デバッグ**選択**ログの有効化**です。 ワークフローが実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
5.  Ctrl + Shift + B キーを押してワークフロー アプリケーションを実行します。  
  
6.  イベント ビューアーで、1009 の ID を持つ最近のイベント、および次のようなメッセージを探します。 メッセージがログに記録された時刻を書き留めます。  
  
 **Parent Activity '、DisplayName: '、InstanceId: ' スケジュール済み子アクティビティ 'WorkflowDurationTracking.Workflow1'、DisplayName: 'Workflow1'、InstanceId: '1' です。**  
  
7.  さらに、1001 の ID を持つ最近のイベント、および次のようなメッセージを探します。  このメッセージのログに記録された値から前のメッセージの時刻を差し引いてワークフロー実行時間を決定します。この時間は約 10 秒になります。  
  
 **WorkflowInstance Id: ' 1bbac57b-3322-498e-9e27-8833fda3a5bf' が Closed 状態で完了しました。**  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー トレース](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [アプリケーション App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201275)
