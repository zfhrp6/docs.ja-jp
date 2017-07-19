---
title: "方法: ステート マシン ワークフローを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 方法: ステート マシン ワークフローを作成する
ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。このトピックでは、<xref:System.Activities.Statements.StateMachine> アクティビティなどのビルトイン アクティビティ、および前の「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」トピックのカスタム アクティビティの両方を使用するワークフローを作成します。このワークフローは、数値推測ゲームをモデル化しています。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。このトピックを完了する前に、「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」を完了する必要があります。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「[Windows Workflow Foundation \(WF45\) \- チュートリアル入門](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### ワークフローを作成するには  
  
1.  **ソリューション エクスプローラー**で **NumberGuessWorkflowActivities** を右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
2.  **\[インストール済み\]** の **\[共通項目\]** ノードで、**\[ワークフロー\]** を選択します。**\[ワークフロー\]** リストで **\[アクティビティ\]** を選択します。  
  
3.  **\[名前\]** ボックスに「`StateMachineNumberGuessWorkflow`」と入力し、**\[追加\]** をクリックします。  
  
4.  **ツールボックス**の **\[ステート マシン\]** セクションから **StateMachine** アクティビティをドラッグし、ワークフロー デザイン サーフェイスの **\[ここにアクティビティをドロップ\]** ラベル上にドロップします。  
  
### ワークフロー変数および引数を作成するには  
  
1.  **ソリューション エクスプローラー**で **StateMachineNumberGuessWorkflow.xaml** をダブルクリックし、デザイナーでワークフローを表示します \(まだ表示されていない場合\)。  
  
2.  ワークフロー デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを表示します。  
  
3.  **\[引数の作成\]** をクリックします。  
  
4.  **\[名前\]** ボックスに「`MaxNumber`」と入力し、**\[方向\]** ボックスで **\[IN\]** を選択して、**\[引数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して引数を保存します。  
  
5.  **\[引数の作成\]** をクリックします。  
  
6.  新しく追加した `MaxNumber` 引数の下にある **\[名前\]** ボックスに「`Turns`」と入力し、**\[方向\]** ボックスで **\[OUT\]** を選択して、**\[引数の型\]** ドロップダウン リストで **\[Int32\]** を選択し、Enter キーを押します。  
  
7.  アクティビティ デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを閉じます。  
  
8.  ワークフロー デザイナーの左下にある **\[変数\]** をクリックし、**\[変数\]** ペインを表示します。  
  
9. **\[変数の作成\]** をクリックします。  
  
    > [!TIP]
    >  **\[変数の作成\]** ボックスが表示されていない場合は、ワークフロー デザイナー画面の <xref:System.Activities.Statements.StateMachine> アクティビティをクリックして選択します。  
  
10. **\[名前\]** ボックスに「`Guess`」と入力し、**\[変数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して変数を保存します。  
  
11. **\[変数の作成\]** をクリックします。  
  
12. **\[名前\]** ボックスに「`Target`」と入力し、**\[変数の型\]** ボックスで **\[Int32\]** を選択し、Enter キーを押して変数を保存します。  
  
13. アクティビティ デザイナーの左下にある **\[変数\]** をクリックし、**\[変数\]** ペインを閉じます。  
  
### ワークフロー アクティビティを追加するには  
  
1.  **\[State1\]** をクリックして選択します。**\[プロパティ\] ウィンドウ**で、**DisplayName** を「`Initialize Target`」に変更します。  
  
    > [!TIP]
    >  **\[プロパティ\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[プロパティ ウィンドウ\]** を選択します。  
  
2.  ワークフロー デザイナーで、名前を **\[Initialize Target\]** に変更した状態をダブルクリックして展開します。  
  
3.  **ツールボックス**の **\[プリミティブ\]** セクションから **Assign** アクティビティをドラッグし、状態の **Entry** セクションにドロップします。**\[終端側\]** ボックスに「`Target`」と入力し、**\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに次の式を入力します。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  **\[ツールボックス\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[ツールボックス\]** をクリックします。  
  
4.  ワークフロー デザイナーの上部にある階層リンク表示の **\[StateMachine\]** をクリックして、ワークフロー デザイナーの全体的なステート マシン ビューに戻ります。  
  
5.  **ツールボックス**の **\[ステート マシン\]** セクションから **State** アクティビティをワークフロー デザイナー上にドラッグし、**Initialize Target** 状態の上に置きます。新しい状態が上に置かれると、**Initialize Target** 状態の周囲に 4 つの三角形が表示されることに注意してください。**Initialize Target** 状態のすぐ下にある三角形の上に、新しい状態をドロップします。これにより、新しい状態がワークフロー上に配置され、**Initialize Target** 状態から新しい状態への遷移が作成されます。  
  
6.  **\[State1\]** をクリックして選択し、**DisplayName** を「`Enter Guess`」に変更して、ワークフロー デザイナーでその状態をダブルクリックして展開します。  
  
7.  **ツールボックス**の **\[プリミティブ\]** セクションから **WriteLine** アクティビティをドラッグし、状態の **Entry** セクションの上にドロップします。  
  
8.  **WriteLine** の **\[Text\]** プロパティ ボックスに次の式を入力します。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. **ツールボックス**の **\[プリミティブ\]** セクションから **Assign** アクティビティをドラッグし、状態の **Exit** セクションにドロップします。  
  
10. **\[終端側\]** ボックスに「`Turns`」と入力し、**\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに「`Turns + 1`」と入力します。  
  
11. ワークフロー デザイナーの上部にある階層リンク表示の **\[StateMachine\]** をクリックして、ワークフロー デザイナーの全体的なステート マシン ビューに戻ります。  
  
12. **ツールボックス**の **\[ステート マシン\]** セクションから **FinalState** アクティビティをドラッグして **Enter Guess** 状態の上にマウス ポインターを置き、**Enter Guess** 状態の右側に表示される三角形の上にドロップすると、**Enter Guess** と **FinalState** の間に遷移が作成されます。  
  
13. 遷移の既定名は **T2** です。ワークフロー デザイナーでその遷移をクリックして選択し、その **DisplayName** に「**Guess Correct**」を設定します。その後、**FinalState** をクリックして選択し、それを右方向へドラッグして、遷移名全体が 2 つの状態のどちらにも重ならずに表示されるようにします。これにより、チュートリアルの残りの手順をより簡単に実行できます。  
  
14. ワークフロー デザイナーで、新しい名前に変更された **Guess Correct** 遷移をダブルクリックして展開します。  
  
15. **ツールボックス**の **\[NumberGuessWorkflowActivities\]** セクションから **ReadInt** アクティビティをドラッグして遷移の **Trigger** セクションにドロップします。  
  
16. **ReadInt** アクティビティの **\[プロパティ\] ウィンドウ**で、**\[BookmarkName\]** プロパティ値ボックスに「`"EnterGuess"`」\(引用符を含む\) と入力し、**\[Result\]** プロパティ値ボックスに「`Guess`」と入力します。  
  
17. **Guess Correct** 遷移の **\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. ワークフロー デザイナーの上部にある階層リンク表示の **\[StateMachine\]** をクリックして、ワークフロー デザイナーの全体的なステート マシン ビューに戻ります。  
  
    > [!NOTE]
    >  トリガー イベントが受け取られ、<xref:System.Activities.Statements.Transition.Condition%2A> \(存在する場合\) が `True` と評価される場合に遷移が発生します。この遷移では、ユーザーの `Guess` がランダムに生成された `Target` と一致する場合、制御が **FinalState** に渡され、ワークフローが完了します。  
  
19. 推定値が正しいかどうかに応じて、ワークフローは **FinalState** に遷移するか、もう一度実行するために **Enter Guess** 状態に戻る必要があります。両方の遷移では、**ReadInt** アクティビティを介して受け取るユーザーの推定値を待機するのに同じトリガーを共有します。これは、共有遷移と呼ばれます。共有遷移を作成するには、**Guess Correct** 遷移の始点を示す円をクリックし、目的の状態にドラッグします。この場合、これは自己遷移であるため、**Guess Correct** 遷移の始点をドラッグし、**Enter Guess** 状態の下にドロップします。遷移の作成後、ワークフロー デザイナーでその遷移を選択し、**DisplayName** プロパティに **Guess Incorrect** を設定します。  
  
    > [!NOTE]
    >  共有遷移は、遷移デザイナー内から作成することもできます。これには、遷移デザイナーの下部にある **\[トリガーを共有する遷移の追加\]** をクリックし、**\[接続の使用可能な状態\]** ボックスの一覧で、目的となる対象の状態を選択します。  
  
    > [!NOTE]
    >  遷移の <xref:System.Activities.Statements.Transition.Condition%2A> が `false` と評価された場合 \(またはトリガーを共有する遷移すべての状態が `false` と評価された場合\)、遷移は行われず、その状態からのすべての遷移のすべてのトリガーが再スケジュールされます。このチュートリアルでは、条件の構成方法 \(推定値が正しいか間違っているかを判断する特定のアクションが用意されています\) により、この状況は発生しません。  
  
20. ワークフロー デザイナーで **Guess Incorrect** 遷移をダブルクリックして展開します。**Trigger** は、**Guess Correct** 遷移で使用されたのと同じ **ReadInt** アクティビティに既に設定されていることに注意してください。  
  
21. **\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. **ツールボックス**の **\[制御フロー\]** セクションから **If** アクティビティをドラッグして遷移の **Action** セクションにドロップします。  
  
23. **If** アクティビティの **\[Condition\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
24. **ツールボックス**の **\[プリミティブ\]** セクションから 2 つの **WriteLine** アクティビティをドラッグし、1 つは **If** アクティビティの **Then** セクション内に、もう 1 つは **Else** セクション内に配置されるようにドロップします。  
  
25. **Then** セクションの **WriteLine** アクティビティをクリックして選択し、**\[Text\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    "Your guess is too low."  
    ```  
  
26. **Else** セクションの **WriteLine** アクティビティをクリックして選択し、**\[Text\]** プロパティ値ボックスに次の式を入力します。  
  
    ```vb-c#  
    "Your guess is too high."  
    ```  
  
27. ワークフロー デザイナーの上部にある階層リンク表示の **\[StateMachine\]** をクリックして、ワークフロー デザイナーの全体的なステート マシン ビューに戻ります。  
  
     次の例は完成したワークフローを示しています。  
  
     ![完成したステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### ワークフローをビルドするには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     ワークフローを実行する手順については、次のトピック「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」を参照してください。「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」の手順を別のスタイルのワークフローを使用して既に完了している場合に、この手順のステート マシンのワークフローを使用して実行するには、「[ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)」の「[アプリケーションをビルドして実行するには](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication)」に進んでください。  
  
## 参照  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Windows Workflow Foundation プログラミングの新機能](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [ワークフローの設計](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)