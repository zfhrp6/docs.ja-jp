---
title: 手続き型アクティビティの使用
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: 787e61a989cb5769461f5155738520dea4609d1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-procedural-activities"></a>手続き型アクティビティの使用
このサンプルでは、<xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Assign>、<xref:System.Activities.Statements.If>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.Switch%601>、<xref:System.Activities.Statements.TryCatch>、および <xref:System.Activities.Statements.WriteLine> の各アクティビティを使用して推測ゲームを実装します。 推測ゲームではランダムな数値が選択され、プレーヤーはその数値を推測する必要があります。 プレーヤーが送信した推測が間違っていると、ワークフローは、その値が正解よりも上か下かを示すヒントを提供します。 プレーヤーが 7 回未満で数値を推測できた場合は、特別な祝福のメッセージがユーザーに表示されます。  
  
## <a name="custom-activities-in-this-sample"></a>このサンプルのカスタム アクティビティ  
  
### <a name="readline"></a>ReadLine  
 コンソールからテキスト行を読み取ります。 このアクティビティは <xref:System.Activities.NativeActivity> クラスから派生し、行が読み取られるときにコンソール アプリケーションによって再開されるブックマークを作成します。  
  
### <a name="promptint"></a>PromptInt  
 ユーザーに数値の入力を求めるメッセージを表示し、その数値をコンソール ウィンドウから読み取ります。 このアクティビティは <xref:System.Activities.Activity%601> から派生し、<xref:System.Activities.Statements.WriteLine> アクティビティと `ReadLine` アクティビティを使用します。  
  
##### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、GuessingGame.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`