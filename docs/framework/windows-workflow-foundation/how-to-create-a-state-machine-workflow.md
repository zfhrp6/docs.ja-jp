---
title: "方法: ステート マシン ワークフローを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 797cdc425c0f3088aa2b75c0285ca6bea2dd425b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a>方法: ステート マシン ワークフローを作成する
ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。 など、両方の組み込みのアクティビティを使用するワークフローを作成する手順をこのトピックの内容、<xref:System.Activities.Statements.StateMachine>アクティビティ、およびカスタム アクティビティを以前から[する方法: アクティビティを作成](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)トピックです。 このワークフローは、数値推測ゲームをモデル化しています。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。 このトピックの内容を完了する必要があります最初に完了する[する方法: アクティビティを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)です。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### <a name="to-create-the-workflow"></a>ワークフローを作成するには  
  
1.  右クリック**NumberGuessWorkflowActivities**で**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の**します。  
  
2.  **インストール**、**共通項目**ノードで、選択**ワークフロー**です。 選択**アクティビティ**から、**ワークフロー**  ボックスの一覧です。  
  
3.  型`StateMachineNumberGuessWorkflow`に、**名前**ボックスし、をクリックして**追加**です。  
  
4.  ドラッグ、 **StateMachine**からアクティビティ、**ステート マシン**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**ラベルワークフロー デザイン サーフェイスです。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>ワークフロー変数および引数を作成するには  
  
1.  ダブルクリックして**StateMachineNumberGuessWorkflow.xaml**で**ソリューション エクスプ ローラー**をまだ表示されていない場合、デザイナーでワークフローを表示します。  
  
2.  をクリックして**引数**を表示するワークフロー デザイナーの左下横で、**引数**ウィンドウです。  
  
3.  をクリックして**引数の作成**です。  
  
4.  型`MaxNumber`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、 **Int32** から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。  
  
5.  をクリックして**引数の作成**です。  
  
6.  型`Turns`に、**名前**、新しく追加した下にあるボックス`MaxNumber`引数で、**アウト**から、**方向**selectドロップダウンリスト**Int32**から、**引数の型**ドロップダウン リストとし、ENTER キーを押します。  
  
7.  をクリックして**引数**を閉じる、アクティビティ デザイナーの左下横で、**引数**ウィンドウです。  
  
8.  をクリックして**変数**を表示するワークフロー デザイナーの左下横で、**変数**ウィンドウです。  
  
9. をクリックして**変数を作成**です。  
  
    > [!TIP]
    >  ない場合は**変数の作成**ボックスが表示されたら、をクリックして、<xref:System.Activities.Statements.StateMachine>それを選択するには、ワークフロー デザイナー画面上のアクティビティ。  
  
10. 型`Guess`に、**名前**ボックスで、 **Int32**から、**変数型**ドロップダウン リスト、および、変数を保存するには ENTER キーを押します。  
  
11. をクリックして**変数を作成**です。  
  
12. 型`Target`に、**名前**ボックスで、 **Int32**から、**変数型**ドロップダウン リスト、および、変数を保存するには ENTER キーを押します。  
  
13. をクリックして**変数**を閉じる、アクティビティ デザイナーの左下横で、**変数**ウィンドウです。  
  
### <a name="to-add-the-workflow-activities"></a>ワークフロー アクティビティを追加するには  
  
1.  をクリックして**State1**をオンにします。 **プロパティ ウィンドウ**、変更、 **DisplayName**に`Initialize Target`です。  
  
    > [!TIP]
    >  場合、**プロパティ ウィンドウ**が表示されていない select**プロパティ ウィンドウ**から、**ビュー**メニュー。  
  
2.  新しく名前を変更 をダブルクリック**Initialize Target**展開ワークフロー デザイナーでの状態。  
  
3.  ドラッグ、**割り当てる**からアクティビティ、**プリミティブ**のセクション、**ツールボックス**上にドロップし、**エントリ**状態のセクションでします。 型`Target`に、**に**ボックスおよびに次の式、 **c# 式を入力**または**VB の式を入力**ボックス。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。  
  
4.  全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。  
  
5.  ドラッグ、**状態**からアクティビティを**ステート マシン**のセクションで、**ツールボックス**、ワークフロー デザイナーに上に置きます、 **Initialize Target**状態です。 周囲に 4 つの三角形が表示されることに注意してください、 **Initialize Target**新しい状態が上にあるときの状態。 新しい状態のすぐ下にある三角形をドロップ、 **Initialize Target**状態です。 これは、新しい状態がワークフロー上に配置しから遷移が作成、 **Initialize Target**新しい状態にします。  
  
6.  をクリックして**State1**選択、変更、 **DisplayName**に`Enter Guess`、し、展開ワークフロー デザイナーでその状態をダブルクリックします。  
  
7.  ドラッグ、 **WriteLine**からアクティビティ、**プリミティブ**のセクションで、**ツールボックス**上にドロップし、**エントリ**状態のセクションでします。  
  
8.  次の式を入力、**テキスト**プロパティ ボックスの**WriteLine**です。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. ドラッグ、**割り当てる**からアクティビティ、**プリミティブ**のセクションで、**ツールボックス**にドロップし、**終了**状態のセクションでします。  
  
10. 型`Turns`に、**に**ボックスおよび`Turns + 1`に、 **c# 式を入力**または**VB の式を入力**ボックス。  
  
11. 全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。  
  
12. ドラッグ、 **FinalState**からアクティビティを**ステート マシン**のセクションで、**ツールボックス**、上にマウス ポインター、 **Enter Guess**状態、および削除右側に表示される三角形の上に、 **Enter Guess**状態の間の遷移が作成されるように**Enter Guess**と**FinalState**です。  
  
13. 遷移の既定の名前は**T2**です。 選択し、設定するには、ワークフロー デザイナーで遷移をクリックしてその**DisplayName**に**Guess Correct**です。 クリックし、選択、 **FinalState**遷移名全体を 2 つの状態のどちらにも重ならずに表示するための領域があるように、右側にドラッグします。 これにより、チュートリアルの残りの手順をより簡単に実行できます。  
  
14. 新しく名前を変更 をダブルクリック**Guess Correct**展開ワークフロー デザイナーで遷移します。  
  
15. ドラッグ、 **ReadInt**からアクティビティを**NumberGuessWorkflowActivities**のセクションで、**ツールボックス**内にドロップし、**トリガー**セクション移行。  
  
16. **プロパティ ウィンドウ**の**ReadInt**アクティビティで、「`"EnterGuess"`に引用符を含む、 **BookmarkName**プロパティ値ボックス、および種類`Guess`に、**結果**プロパティ値ボックス  
  
17. 次の式を入力、 **Guess Correct**遷移の**条件**プロパティ値ボックスです。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。  
  
    > [!NOTE]
    >  トリガー イベントが受け取られ、<xref:System.Activities.Statements.Transition.Condition%2A> (存在する場合) が `True` と評価される場合に遷移が発生します。 この遷移の場合、ユーザーの`Guess`ランダムに生成されると一致する`Target`、制御が渡されますし、 **FinalState**ワークフローが完了するとします。  
  
19. によっては、推定値が正しいかどうか、ワークフローが遷移するか、 **FinalState**またはに戻し、 **Enter Guess**もう一度実行状態。 両方の遷移がユーザーの推定値経由で受信を待機しているに同じトリガーを共有、 **ReadInt**アクティビティ。 これは、共有遷移と呼ばれます。 共有遷移を作成するには、開始を示す円をクリックして、 **Guess Correct**に移行し、目的の状態にドラッグします。 この場合は自己遷移には、そのための開始点をドラッグ、 **Guess Correct**の下にドロップになり、 **Enter Guess**状態です。 遷移を作成すると、ワークフロー デザイナーで選択し、設定、 **DisplayName**プロパティを**Guess Incorrect**です。  
  
    > [!NOTE]
    >  共有遷移できますも作成することから、遷移デザイナー内をクリックして**共有トリガー遷移の追加**から目的のターゲットの状態をクリックして、遷移デザイナーの下部にある、 **接続に使用可能な状態**ドロップダウンします。  
  
    > [!NOTE]
    >  遷移の <xref:System.Activities.Statements.Transition.Condition%2A> が `false` と評価された場合 (またはトリガーを共有する遷移すべての状態が `false` と評価された場合)、遷移は行われず、その状態からのすべての遷移のすべてのトリガーが再スケジュールされます。 このチュートリアルでは、条件の構成方法 (推定値が正しいか間違っているかを判断する特定のアクションが用意されています) により、この状況は発生しません。  
  
20. ダブルクリックして、 **Guess Incorrect**展開ワークフロー デザイナーで遷移します。 注意してください、**トリガー**は既に同じに設定**ReadInt**アクティビティで使用されていた、 **Guess Correct**遷移します。  
  
21. 次の式を入力、**条件**プロパティ値ボックスです。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. ドラッグ、**場合**からアクティビティ、**制御フロー**のセクションで、**ツールボックス**内にドロップし、**アクション**遷移のセクションでします。  
  
23. 次の式を入力、**場合**アクティビティの**条件**プロパティ値ボックスです。  
  
    ```
    Guess < Target  
    ```  
  
24. 2 つをドラッグして**WriteLine**からアクティビティを**プリミティブ**のセクション、**ツールボックス**が 1 つになるようにドロップして、**し**のセクション**場合**、もう 1 つでは、 **Else**セクションです。  
  
25. クリックして、 **WriteLine**内のアクティビティ、**し**して選択し、セクションし、次の式を入力、**テキスト**プロパティ値ボックスです。  
  
    ```
    "Your guess is too low."  
    ```  
  
26. クリックして、 **WriteLine**内のアクティビティ、 **Else**して選択し、セクションし、次の式を入力、**テキスト**プロパティ値ボックスです。  
  
    ```
    "Your guess is too high."  
    ```  
  
27. 全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。  
  
     次の例は完成したワークフローを示しています。  
  
     ![完成したステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>ワークフローをビルドするには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     ワークフローを実行する方法については、次のトピックをご覧ください。[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)です。 既に完了している場合、[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)ステップのワークフローとは異なるスタイルと共に、この手順で、ステート マシン ワークフローを使用して実行してに進んで、[アプリケーションをビルドして実行](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)のセクション[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation プログラミング](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [ワークフローの設計](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [ワークフローを実行する方法](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
