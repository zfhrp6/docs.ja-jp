---
title: 簡単なポリシー
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: dff3979d75fdeb5a45be3940af3568c26f5e8f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515897"
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
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [高度なポリシー](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
