---
title: CancellationScope の使用
ms.date: 03/30/2017
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
ms.openlocfilehash: 62b798b29149e30a2fae680b507f62ef0a2e23d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-cancellationscope"></a>CancellationScope の使用
このサンプルでは、<xref:System.Activities.Statements.CancellationScope> アクティビティを使用してアプリケーション内の処理を取り消す方法を示します。  
  
 中間層のコンポーネントやサービスの多くでは、既知のプログラミング構成要素であるトランザクションを使用して取り消しを処理します。  ただし、トランザクションでは実行できない処理を取り消さなければならない場合も数多くあります。  取り消しを使用することがトランザクションを使用することよりも難しいのは、取り消す必要がある処理を先に追跡しなければならないからです。 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] には、この処理に役立つ <xref:System.Activities.Statements.CancellationScope> アクティビティが用意されています。  
  
 取り消しはアクティビティ内またはアクティビティの親からトリガーできます。  子アクティビティは、親アクティビティ (<xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Parallel>、<xref:System.Activities.Statements.Flowchart>、またはカスタム複合アクティビティ) によってスケジュールされます。  親アクティビティは、どのような理由でも子アクティビティを取り消すことができます。  たとえば、3 つの子分岐がある <xref:System.Activities.Statements.Parallel> アクティビティでは、1 つの分岐が完了し、<xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 式の評価結果が `true` であれば、残りの子分岐を取り消します。 ワークフローは、ホスト アプリケーションで <xref:System.Activities.WorkflowApplication.Cancel%2A> を呼び出すことで外部から取り消すこともできます。  
  
 <xref:System.Activities.Statements.CancellationScope> アクティビティを使用するには、取り消す必要がある処理を <xref:System.Activities.Statements.CancellationScope.Body%2A> プロパティに設定し、取り消し後に実行する処理を <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> プロパティに設定します。  
  
 このサンプルでは、アクティビティ自体からアクティビティを取り消す方法を示します。  
  
 このサンプルでは、マイアミ行きのチケットをできるだけ早く購入する必要があるクライアントのシナリオを使用して、<xref:System.Activities.Statements.CancellationScope> アクティビティの例を示します。 取り引きを検討している旅行代理店が 2 社あり、 このビジネス ロジックを、<xref:System.Activities.Statements.CancellationScope> アクティビティ内の 2 つの <xref:System.Activities.Statements.Parallel> を使用してモデル化しています。 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> アクティビティの <xref:System.Activities.Statements.Parallel> は `true` に設定されています。分岐の完了後に <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> が確認されるため、最初の分岐が完了すると残りの分岐が取り消されます。 クライアント アプリケーションは、両方の代理店にチケットを注文し、どちらかでチケットを購入できた時点でもう一方の代理店の注文を取り消します。  
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CancelationScopeXAML.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`