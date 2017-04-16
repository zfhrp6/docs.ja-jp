---
title: "シーケンシャル ワークフローを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# シーケンシャル ワークフローを作成する方法
ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。このトピックでは、<xref:System.Activities.Statements.Sequence> アクティビティなどのビルトイン アクティビティ、および前の「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」トピックのカスタム アクティビティの両方を使用するワークフローを作成します。このワークフローは、数値推測ゲームをモデル化しています。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。このトピックを完了する前に、「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」を完了する必要があります。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「[Windows Workflow Foundation \(WF45\) \- チュートリアル入門](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### ワークフローを作成するには  
  
1.  **ソリューション エクスプローラー**で **NumberGuessWorkflowActivities** を右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
2.  **\[インストール済み\]** の **\[共通項目\]** ノードで、**\[ワークフロー\]** を選択します。**\[ワークフロー\]** リストで **\[アクティビティ\]** を選択します。  
  
3.  **\[名前\]** ボックスに「`SequentialNumberGuessWorkflow`」と入力し、**\[追加\]** をクリックします。  
  
4.  **ツールボックス**の **\[制御フロー\]** セクションから **Sequence** アクティビティをドラッグし、ワークフロー デザイン サーフェイスの **\[ここにアクティビティをドロップ\]** ラベルの上にドロップします。  
  
### ワークフロー変数および引数を作成するには  
  
1.  **ソリューション エクスプローラー**で **SequentialNumberGuessWorkflow.xaml** をダブルクリックし、デザイナーにワークフローを表示します \(まだ表示されていない場合\)。  
  
2.  ワークフロー デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを表示します。  
  
3.  **\[引数の作成\]** をクリックします。  
  
4.  **\[名前\]** ボックスに「`MaxNumber`」と入力し、**\[方向\]** ボックスで **\[IN\]** を選択して、**\[引数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して引数を保存します。  
  
5.  **\[引数の作成\]** をクリックします。  
  
6.  新しく追加した `MaxNumber` 引数の下にある **\[名前\]** ボックスに「`Turns`」と入力し、**\[方向\]** ボックスで **\[OUT\]** を選択して、**\[引数の型\]** ドロップダウン リストで **\[Int32\]** を選択し、Enter キーを押します。  
  
7.  アクティビティ デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを閉じます。  
  
8.  ワークフロー デザイナーの左下にある **\[変数\]** をクリックし、**\[変数\]** ペインを表示します。  
  
9. **\[変数の作成\]** をクリックします。  
  
    > [!TIP]
    >  **\[変数の作成\]** ボックスが表示されていない場合は、ワークフロー デザイナー画面の **Sequence** アクティビティをクリックして選択します。  
  
10. **\[名前\]** ボックスに「`Guess`」と入力し、**\[変数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して変数を保存します。  
  
11. **\[変数の作成\]** をクリックします。  
  
12. **\[名前\]** ボックスに「`Target`」と入力し、**\[変数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して変数を保存します。  
  
13. アクティビティ デザイナーの左下にある **\[変数\]** をクリックし、**\[変数\]** ペインを閉じます。  
  
### ワークフロー アクティビティを追加するには  
  
1.  **ツールボックス**の **\[プリミティブ\]** セクションから **Assign** アクティビティをドラッグし、**Sequence** アクティビティにドロップします。**\[終端側\]** ボックスに「`Target`」と入力し、**\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに次の式を入力します。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  **\[ツールボックス\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[ツールボックス\]** をクリックします。  
  
2.  **ツールボックス**の **\[制御フロー\]** セクションから **DoWhile** アクティビティをドラッグし、ワークフロー上の **Assign** アクティビティの下にドロップします。  
  
3.  **DoWhile** アクティビティの **\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <xref:System.Activities.Statements.DoWhile> アクティビティはその子アクティビティを実行し、その <xref:System.Activities.Statements.DoWhile.Condition%2A> を評価します。<xref:System.Activities.Statements.DoWhile.Condition%2A> が `True` と評価される場合、<xref:System.Activities.Statements.DoWhile> 内のアクティビティが再度実行されます。この例では、ユーザーの推定値が評価され、推定値が正しいと判断されるまで <xref:System.Activities.Statements.DoWhile> が続行されます。  
  
4.  **ツールボックス**の **\[NumberGuessWorkflowActivities\]** セクションから **Prompt** アクティビティをドラッグし、前の手順の **DoWhile** アクティビティの下にドロップします。  
  
5.  **\[プロパティ\] ウィンドウ**で、**Prompt** アクティビティの **\[BookmarkName\]** プロパティ値ボックスに「`"EnterGuess"`」\(引用符を含む\) と入力します。**\[Result\]** プロパティ値ボックスに「`Guess`」と入力し、**\[Text\]** プロパティ ボックスに次の式を入力します。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  **\[プロパティ\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[プロパティ ウィンドウ\]** を選択します。  
  
6.  **ツールボックス**の **\[プリミティブ\]** セクションから **Assign** アクティビティをドラッグし、**Prompt** アクティビティの後になるように **DoWhile** アクティビティ内にドロップします。  
  
    > [!NOTE]
    >  **Assign** アクティビティをドロップするときに、ワークフロー デザイナーによって、**Prompt** アクティビティと新しく追加した **Assign** アクティビティの両方を含む **Sequence** アクティビティが自動的に追加されることに注意してください。  
  
7.  **\[終端側\]** ボックスに「`Turns`」と入力し、**\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに「`Turns + 1`」と入力します。  
  
8.  **ツールボックス**の **\[制御フロー\]** セクションから **If** アクティビティをドラッグし、新しく追加した **Assign** アクティビティの後になるように **Sequence** アクティビティ内にドロップします。  
  
9. **If** アクティビティの **\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. **ツールボックス**の **\[制御フロー\]** セクションから **If** アクティビティをドラッグし、最初の **If** アクティビティの **Then** セクションにドロップします。  
  
11. 新しく追加した **If** アクティビティの **\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
12. **ツールボックス**の **\[プリミティブ\]** セクションから 2 つの **WriteLine** アクティビティをドラッグし、1 つは新しく追加した **If** アクティビティの **Then** セクション内に、もう 1 つは **Else** セクション内に配置されるようにドロップします。  
  
13. **Then** セクションの **WriteLine** アクティビティをクリックして選択し、**\[Text\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. **Else** セクションの **WriteLine** アクティビティをクリックして選択し、**\[Text\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     次の例は完成したワークフローを示しています。  
  
     ![完成したシーケンシャル ワークフロー](../../../docs/framework/windows-workflow-foundation//media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### ワークフローをビルドするには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     ワークフローを実行する手順については、次のトピック「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」を参照してください。「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」の手順を別のスタイルのワークフローを使用して既に完了している場合に、この手順のシーケンシャル ワークフローを使用して実行するには、「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」の「[アプリケーションをビルドして実行するには](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication)」に進んでください。  
  
## 参照  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Windows Workflow Foundation プログラミングの新機能](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [ワークフローの設計](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)