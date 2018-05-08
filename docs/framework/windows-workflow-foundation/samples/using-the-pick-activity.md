---
title: Pick アクティビティの使用
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 9617949d72fb1489f66fec205b260b807d011177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-pick-activity"></a>Pick アクティビティの使用
このサンプルでは、<xref:System.Activities.Statements.Pick> アクティビティを使用する方法を示します。  
  
 <xref:System.Activities.Statements.Pick> アクティビティでは、イベント ベースの制御モデリングを提供します。 このアクティビティの動作は C# の `switch` ステートメントに似ています。`switch` ステートメントでは、その分岐のうち 1 つだけが実行されます。 ただし、値に基づいて分岐が実行される `switch` ステートメントと異なり、<xref:System.Activities.Statements.Pick> アクティビティでは、アクティビティの完了の状態に基づいて分岐を実行します。  
  
 このサンプルでは、指定した時間内にコンソールでユーザー名を入力するようユーザーに求めます。 このサンプルの <xref:System.Activities.Statements.Pick> アクティビティには、ユーザーが 5 秒以内にユーザー名を入力したかどうかに基づいて実行される 2 つの分岐があります。 ユーザーが 5 秒以内にユーザー名を入力した場合は、カスタムの `ReadLine` アクティビティを含む最初の分岐が実行されます。それ以外の場合は、<xref:System.Activities.Statements.Delay> アクティビティを含むもう 1 つの分岐が実行されます。 コンソールでユーザー名を入力すると、そのユーザー名がコンソールに出力されます。 5 秒以内に入力しないと、操作はタイムアウトします。  
  
## <a name="demonstrates"></a>使用例  
 <xref:System.Activities.Statements.Pick> アクティビティ。  
  
## <a name="discussion"></a>説明  
 このサンプルには、デザイナー ワークフローとコード化されたワークフローがあります。  
  
 デザイナー ワークフロー  
 このサンプルのデザイナー バージョンでは、デザイナーでワークフローを作成する方法を示します。 次のファイルがあります。  
  
-   Program.cs: サンプル ワークフローを実行する `Main` 関数が含まれています。  
  
-   ReadString.cs: コンソールからの入力を読み取るカスタム アクティビティです。  
  
-   Sequence1.xaml: Pick を使用する、デザイナーで作成されたワークフローです。  
  
 コード化されたワークフロー  
 このサンプルのコード化されたバージョンでは、デザイナーでワークフローを作成する方法を示します。 次のファイルがあります。  
  
-   Program.cs: サンプル ワークフローを実行する `Main` 関数が含まれています。  
  
-   ReadString.cs: コンソールからの入力を読み取るカスタム アクティビティです。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、Pick.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`