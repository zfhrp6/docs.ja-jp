---
title: 命令型 TransactionScope でのワークフローの実行
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 44efc13efaa45274068fb44cc154b515bd774a35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>命令型 TransactionScope でのワークフローの実行
このサンプルでは、命令型 C# コードから <xref:System.Activities.WorkflowInvoker> で <xref:System.Transactions.Transaction> を使用してワークフローを実行する方法を示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 命令型 C# コードで、<xref:System.Transactions.TransactionScope> を使用して、同じトランザクションで実行される一連の作業をカプセル化します。 <xref:System.Transactions.TransactionScope> は、アンビエント トランザクションを作成し、<xref:System.Transactions.Transaction.Current%2A> プロパティを初期化することによって機能します。初期化後、このプロパティには、そのスレッドで実行されるどの作業からでもアクセスできます。  
  
 ワークフローではアクティビティ間でスレッド アフィニティが維持されないため、ワークフローで同等の動作を実現するには、ランタイムで、追加の作業として各アクティビティの実行前に <xref:System.Transactions.Transaction.Current%2A> を初期化する必要があります。 このランタイムによるサポートの結果として、<xref:System.Activities.WorkflowInvoker> 内で <xref:System.Transactions.TransactionScope> を使用してワークフローを実行するとき、すべてのアクティビティが、<xref:System.Transactions.TransactionScope> によって作成されたアンビエント トランザクションのコンテキストで実行されるようになります。  
  
 ワークフローではワークフロー インスタンスごとに 1 つのアンビエント トランザクションしか使用できず、入れ子になったトランザクションは使用できません。 ワークフローに <xref:System.Activities.Statements.TransactionScope> アクティビティがある場合でも、新しい内側のトランザクションは作成されません。 代わりに、ワークフロー外で作成されたアンビエント トランザクションが再利用されます。  
  
 このサンプルでは、新しい <xref:System.Transactions.TransactionScope> を開始し、トランザクション ID を出力して、<xref:System.Activities.WorkflowInvoker> によってワークフローを開始します。 ワークフローではトランザクション ID を再度出力し (これにより、同じトランザクションであることが示されます)、<xref:System.Activities.Statements.TransactionScope> を実行して、完了します。 <xref:System.Activities.WorkflowInvoker.Invoke%2A> での <xref:System.Activities.WorkflowInvoker> の呼び出しは同期的であるので、元のスレッドはワークフローが完了するまでブロックされます。 ワークフローが完了すると、トランザクションが完了し、リソースが破棄されます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ImperativeTransactionSample.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`