---
title: "フローチャート ワークフローを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# フローチャート ワークフローを作成する方法
ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。このトピックでは、<xref:System.Activities.Statements.Flowchart> アクティビティなどのビルトイン アクティビティ、および前の「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」トピックのカスタム アクティビティの両方を使用するワークフローを作成します。このワークフローは、数値推測ゲームをモデル化しています。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。このトピックを完了する前に、「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」を完了する必要があります。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「[Windows Workflow Foundation \(WF45\) \- チュートリアル入門](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### ワークフローを作成するには  
  
1.  **ソリューション エクスプローラー**で **NumberGuessWorkflowActivities** を右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
2.  **\[インストール済み\]** の **\[共通項目\]** ノードで、**\[ワークフロー\]** を選択します。**\[ワークフロー\]** リストで **\[アクティビティ\]** を選択します。  
  
3.  **\[名前\]** ボックスに「`FlowchartNumberGuessWorkflow`」と入力し、**\[追加\]** をクリックします。  
  
4.  **ツールボックス**の **\[フローチャート\]** セクションから **Flowchart** アクティビティをドラッグし、ワークフロー デザイン サーフェイスの **\[ここにアクティビティをドロップ\]** ラベルの上にドロップします。  
  
### ワークフロー変数および引数を作成するには  
  
1.  **FlowchartNumberGuessWorkflow.xaml** がまだ表示されていない場合は、**ソリューション エクスプローラー**でダブルクリックして、デザイナーにワークフローを表示します。  
  
2.  ワークフロー デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを表示します。  
  
3.  **\[引数の作成\]** をクリックします。  
  
4.  **\[名前\]** ボックスに「`MaxNumber`」と入力し、**\[方向\]** ボックスで **\[IN\]** を選択して、**\[引数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して引数を保存します。  
  
5.  **\[引数の作成\]** をクリックします。  
  
6.  新しく追加した `MaxNumber` 引数の下にある **\[名前\]** ボックスに「`Turns`」と入力し、**\[方向\]** ボックスで **\[OUT\]** を選択して、**\[引数の型\]** ドロップダウン リストで **\[Int32\]** を選択し、Enter キーを押します。  
  
7.  アクティビティ デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを閉じます。  
  
8.  ワークフロー デザイナーの左下にある **\[変数\]** をクリックし、**\[変数\]** ペインを表示します。  
  
9. **\[変数の作成\]** をクリックします。  
  
    > [!TIP]
    >  **\[変数の作成\]** ボックスが表示されていない場合は、ワークフロー デザイナー画面の <xref:System.Activities.Statements.Flowchart> アクティビティをクリックして選択します。  
  
10. **\[名前\]** ボックスに「`Guess`」と入力し、**\[変数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して変数を保存します。  
  
11. **\[変数の作成\]** をクリックします。  
  
12. **\[名前\]** ボックスに「`Target`」と入力し、**\[変数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して変数を保存します。  
  
13. アクティビティ デザイナーの左下にある **\[変数\]** をクリックし、**\[変数\]** ペインを閉じます。  
  
### ワークフロー アクティビティを追加するには  
  
1.  **ツールボックス**の **\[プリミティブ\]** セクションから **Assign** アクティビティをドラッグし、フローチャートの上部にある **Start** ノード上に置きます。**Assign** アクティビティが **Start** ノード上にあるときに、3 個の三角形が **Start** ノードの周囲に表示されます。**Assign** アクティビティを **Start** ノードのすぐ下にある三角形の上にドロップします。これにより 2 つのアイテムがリンクされ、**Assign** アクティビティがフローチャート内の最初のアクティビティとして指定されます。  
  
    > [!NOTE]
    >  アクティビティは、開始ノードに手動でリンクすることにより、ワークフローの開始アクティビティとして指定することもできます。これを行うには、**Start** ノードをポイントし、**Start** ノードをポイントすると表示される四角形の 1 つをクリックして、目的のアクティビティに線を接続するようにマウスをドラッグし、表示される四角形の 1 つにドロップします。また、アクティビティを右クリックして **\[StartNode として設定\]** を選択して、アクティビティを開始アクティビティとして指定することもできます。  
  
2.  **\[終端側\]** ボックスに「`Target`」と入力し、**\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに次の式を入力します。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  **\[ツールボックス\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[ツールボックス\]** をクリックします。  
  
3.  **ツールボックス**の **\[NumberGuessWorkflowActivities\]** セクションから **Prompt** アクティビティをドラッグし、前の手順でドロップした **Assign** アクティビティの下にドロップして、**Prompt** アクティビティを **Assign** アクティビティに接続します。2 つのアクティビティを接続する方法は 3 種類あります。1 つ目の方法では、**Prompt** アクティビティをワークフロー上にドロップするときにアクティビティを接続します。ワークフローに **Prompt** アクティビティをドラッグするときに、**Assign** アクティビティ上にマウス ポインターを置き、**Prompt** アクティビティが **Assign** のアクティビティ上にあるときに表示される 4 つの三角形の 1 つにドロップします。2 つ目の方法では、ワークフローの希望する位置に **Prompt** アクティビティをドロップします。その後、**Assign** アクティビティにマウス ポインターを置き、表示される四角形の 1 つを **Prompt** アクティビティにドラッグします。**Assign** アクティビティから **Prompt** アクティビティの四角形の 1 つに線を接続するようにマウスをドラッグし、マウスのボタンを離します。3 つ目の方法は 1 つ目の方法とよく似ていますが、**Prompt** アクティビティを**ツールボックス**からドラッグする代わりに、ワークフロー デザイン サーフェイス上のその位置からドラッグし、マウス ポインターを **Assign** アクティビティ上に移動して、表示される三角形の 1 つにドロップします。  
  
4.  **Prompt** アクティビティの **\[プロパティ\] ウィンドウ**で、**\[BookmarkName\]** プロパティ値ボックスに「`"EnterGuess"`」\(引用符を含む\) と入力します。**\[Result\]** プロパティ値ボックスに「`Guess`」と入力し、**\[Text\]** プロパティ ボックスに次の式を入力します。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  **\[プロパティ\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[プロパティ ウィンドウ\]** を選択します。  
  
5.  **ツールボックス**の **\[プリミティブ\]** セクションから **Assign** アクティビティをドラッグし、前の手順で説明した方法のいずれかを使用して、このアクティビティが **Prompt** アクティビティの下になるように接続します。  
  
6.  **\[終端側\]** ボックスに「`Turns`」と入力し、**\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに「`Turns + 1`」と入力します。  
  
7.  **ツールボックス**の **\[フローチャート\]** セクションから **FlowDecision** をドラッグし、**Assign** アクティビティの下に接続します。**\[プロパティ\]** ウィンドウで、**\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  **\[ツールボックス\]** から別の **FlowDecision** アクティビティをドラッグし、最初のアクティビティの下にドロップします。2 つのアクティビティを接続するには、上部の **FlowDecision** アクティビティにある **\[False\]** という四角形から、2 番目の **FlowDecision** アクティビティの上部にある四角形までドラッグします。  
  
    > [!TIP]
    >  **FlowDecision** 上に **\[True\]** および **\[False\]** というラベルが表示されない場合は、**FlowDecision** にマウス ポインターを置きます。  
  
9. 2 番目の **FlowDecision** アクティビティをクリックして選択します。**\[プロパティ\]** ウィンドウで、**\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
10. **\[ツールボックス\]** の **\[プリミティブ\]** セクションから 2 つの **WriteLine** アクティビティをドラッグし、2 つの **FlowDecision** アクティビティの下に並べるようにドロップします。下部の **FlowDecision** アクティビティの **True** アクションを最も左の **WriteLine** に接続し、**False** アクションを最も右の **WriteLine** に接続します。  
  
11. 最も左の **WriteLine** アクティビティをクリックし、**\[プロパティ\]** ウィンドウの **\[Text\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    "Your guess is too low."  
    ```  
  
12. その上にある **Prompt** アクティビティの左側に **WriteLine** を接続します。  
  
13. 最も右の **WriteLine** アクティビティをクリックし、**\[プロパティ\]** ウィンドウの **\[Text\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    "Your guess is too high."  
    ```  
  
14. その上にある **Prompt** アクティビティの右側に **WriteLine** アクティビティを接続します。  
  
     次の例は完成したワークフローを示しています。  
  
     ![完成した Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation//media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### ワークフローをビルドするには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     ワークフローを実行する手順については、次のトピック「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」を参照してください。「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」の手順を別のスタイルのワークフローを使用して既に完了している場合に、この手順のフローチャート ワークフローを使用して実行するには、「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」の「[アプリケーションをビルドして実行するには](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication)」に進んでください。  
  
## 参照  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Windows Workflow Foundation プログラミングの新機能](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [ワークフローの設計](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)