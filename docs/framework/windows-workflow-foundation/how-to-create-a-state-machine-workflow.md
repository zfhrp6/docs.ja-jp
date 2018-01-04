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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95ba37b123b57ba9f86fefb55a860fb2122ccd3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="c979e-102">方法: ステート マシン ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="c979e-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="c979e-103">ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。</span><span class="sxs-lookup"><span data-stu-id="c979e-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="c979e-104">など、両方の組み込みのアクティビティを使用するワークフローを作成する手順をこのトピックの内容、<xref:System.Activities.Statements.StateMachine>アクティビティ、およびカスタム アクティビティを以前から[する方法: アクティビティを作成](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="c979e-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="c979e-105">このワークフローは、数値推測ゲームをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="c979e-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c979e-106">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="c979e-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="c979e-107">このトピックの内容を完了する必要があります最初に完了する[する方法: アクティビティを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)です。</span><span class="sxs-lookup"><span data-stu-id="c979e-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c979e-108">チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c979e-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="c979e-109">ワークフローを作成するには</span><span class="sxs-lookup"><span data-stu-id="c979e-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="c979e-110">右クリック**NumberGuessWorkflowActivities**で**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の**します。</span><span class="sxs-lookup"><span data-stu-id="c979e-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="c979e-111">**インストール**、**共通項目**ノードで、選択**ワークフロー**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="c979e-112">選択**アクティビティ**から、**ワークフロー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="c979e-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="c979e-113">型`StateMachineNumberGuessWorkflow`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="c979e-114">ドラッグ、 **StateMachine**からアクティビティ、**ステート マシン**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**ラベルワークフロー デザイン サーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="c979e-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="c979e-115">ワークフロー変数および引数を作成するには</span><span class="sxs-lookup"><span data-stu-id="c979e-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="c979e-116">ダブルクリックして**StateMachineNumberGuessWorkflow.xaml**で**ソリューション エクスプ ローラー**をまだ表示されていない場合、デザイナーでワークフローを表示します。</span><span class="sxs-lookup"><span data-stu-id="c979e-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="c979e-117">をクリックして**引数**を表示するワークフロー デザイナーの左下横で、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="c979e-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="c979e-118">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="c979e-119">型`MaxNumber`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、 **Int32** から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c979e-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="c979e-120">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="c979e-121">型`Turns`に、**名前**、新しく追加した下にあるボックス`MaxNumber`引数で、**アウト**から、**方向**selectドロップダウンリスト**Int32**から、**引数の型**ドロップダウン リストとし、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c979e-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="c979e-122">をクリックして**引数**を閉じる、アクティビティ デザイナーの左下横で、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="c979e-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="c979e-123">をクリックして**変数**を表示するワークフロー デザイナーの左下横で、**変数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="c979e-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="c979e-124">をクリックして**変数を作成**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c979e-125">ない場合は**変数の作成**ボックスが表示されたら、をクリックして、<xref:System.Activities.Statements.StateMachine>それを選択するには、ワークフロー デザイナー画面上のアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="c979e-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="c979e-126">型`Guess`に、**名前**ボックスで、 **Int32**から、**変数型**ドロップダウン リスト、および、変数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c979e-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="c979e-127">をクリックして**変数を作成**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="c979e-128">型`Target`に、**名前**ボックスで、 **Int32**から、**変数型**ドロップダウン リスト、および、変数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c979e-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="c979e-129">をクリックして**変数**を閉じる、アクティビティ デザイナーの左下横で、**変数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="c979e-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="c979e-130">ワークフロー アクティビティを追加するには</span><span class="sxs-lookup"><span data-stu-id="c979e-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="c979e-131">をクリックして**State1**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="c979e-131">Click **State1** to select it.</span></span> <span data-ttu-id="c979e-132">**プロパティ ウィンドウ**、変更、 **DisplayName**に`Initialize Target`です。</span><span class="sxs-lookup"><span data-stu-id="c979e-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c979e-133">場合、**プロパティ ウィンドウ**が表示されていない select**プロパティ ウィンドウ**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="c979e-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="c979e-134">新しく名前を変更 をダブルクリック**Initialize Target**展開ワークフロー デザイナーでの状態。</span><span class="sxs-lookup"><span data-stu-id="c979e-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="c979e-135">ドラッグ、**割り当てる**からアクティビティ、**プリミティブ**のセクション、**ツールボックス**上にドロップし、**エントリ**状態のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="c979e-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="c979e-136">型`Target`に、**に**ボックスおよびに次の式、 **c# 式を入力**または**VB の式を入力**ボックス。</span><span class="sxs-lookup"><span data-stu-id="c979e-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="c979e-137">場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="c979e-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="c979e-138">全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。</span><span class="sxs-lookup"><span data-stu-id="c979e-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="c979e-139">ドラッグ、**状態**からアクティビティを**ステート マシン**のセクションで、**ツールボックス**、ワークフロー デザイナーに上に置きます、 **Initialize Target**状態です。</span><span class="sxs-lookup"><span data-stu-id="c979e-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="c979e-140">周囲に 4 つの三角形が表示されることに注意してください、 **Initialize Target**新しい状態が上にあるときの状態。</span><span class="sxs-lookup"><span data-stu-id="c979e-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="c979e-141">新しい状態のすぐ下にある三角形をドロップ、 **Initialize Target**状態です。</span><span class="sxs-lookup"><span data-stu-id="c979e-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="c979e-142">これは、新しい状態がワークフロー上に配置しから遷移が作成、 **Initialize Target**新しい状態にします。</span><span class="sxs-lookup"><span data-stu-id="c979e-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="c979e-143">をクリックして**State1**選択、変更、 **DisplayName**に`Enter Guess`、し、展開ワークフロー デザイナーでその状態をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c979e-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="c979e-144">ドラッグ、 **WriteLine**からアクティビティ、**プリミティブ**のセクションで、**ツールボックス**上にドロップし、**エントリ**状態のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="c979e-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="c979e-145">次の式を入力、**テキスト**プロパティ ボックスの**WriteLine**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="c979e-146">ドラッグ、**割り当てる**からアクティビティ、**プリミティブ**のセクションで、**ツールボックス**にドロップし、**終了**状態のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="c979e-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="c979e-147">型`Turns`に、**に**ボックスおよび`Turns + 1`に、 **c# 式を入力**または**VB の式を入力**ボックス。</span><span class="sxs-lookup"><span data-stu-id="c979e-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="c979e-148">全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。</span><span class="sxs-lookup"><span data-stu-id="c979e-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="c979e-149">ドラッグ、 **FinalState**からアクティビティを**ステート マシン**のセクションで、**ツールボックス**、上にマウス ポインター、 **Enter Guess**状態、および削除右側に表示される三角形の上に、 **Enter Guess**状態の間の遷移が作成されるように**Enter Guess**と**FinalState**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="c979e-150">遷移の既定の名前は**T2**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="c979e-151">選択し、設定するには、ワークフロー デザイナーで遷移をクリックしてその**DisplayName**に**Guess Correct**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="c979e-152">クリックし、選択、 **FinalState**遷移名全体を 2 つの状態のどちらにも重ならずに表示するための領域があるように、右側にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c979e-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="c979e-153">これにより、チュートリアルの残りの手順をより簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="c979e-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="c979e-154">新しく名前を変更 をダブルクリック**Guess Correct**展開ワークフロー デザイナーで遷移します。</span><span class="sxs-lookup"><span data-stu-id="c979e-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="c979e-155">ドラッグ、 **ReadInt**からアクティビティを**NumberGuessWorkflowActivities**のセクションで、**ツールボックス**内にドロップし、**トリガー**セクション移行。</span><span class="sxs-lookup"><span data-stu-id="c979e-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="c979e-156">**プロパティ ウィンドウ**の**ReadInt**アクティビティで、「`"EnterGuess"`に引用符を含む、 **BookmarkName**プロパティ値ボックス、および種類`Guess`に、**結果**プロパティ値ボックス</span><span class="sxs-lookup"><span data-stu-id="c979e-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="c979e-157">次の式を入力、 **Guess Correct**遷移の**条件**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="c979e-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="c979e-158">全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。</span><span class="sxs-lookup"><span data-stu-id="c979e-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c979e-159">トリガー イベントが受け取られ、<xref:System.Activities.Statements.Transition.Condition%2A> (存在する場合) が `True` と評価される場合に遷移が発生します。</span><span class="sxs-lookup"><span data-stu-id="c979e-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="c979e-160">この遷移の場合、ユーザーの`Guess`ランダムに生成されると一致する`Target`、制御が渡されますし、 **FinalState**ワークフローが完了するとします。</span><span class="sxs-lookup"><span data-stu-id="c979e-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="c979e-161">によっては、推定値が正しいかどうか、ワークフローが遷移するか、 **FinalState**またはに戻し、 **Enter Guess**もう一度実行状態。</span><span class="sxs-lookup"><span data-stu-id="c979e-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="c979e-162">両方の遷移がユーザーの推定値経由で受信を待機しているに同じトリガーを共有、 **ReadInt**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="c979e-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="c979e-163">これは、共有遷移と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c979e-163">This is called a shared transition.</span></span> <span data-ttu-id="c979e-164">共有遷移を作成するには、開始を示す円をクリックして、 **Guess Correct**に移行し、目的の状態にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c979e-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="c979e-165">この場合は自己遷移には、そのための開始点をドラッグ、 **Guess Correct**の下にドロップになり、 **Enter Guess**状態です。</span><span class="sxs-lookup"><span data-stu-id="c979e-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="c979e-166">遷移を作成すると、ワークフロー デザイナーで選択し、設定、 **DisplayName**プロパティを**Guess Incorrect**です。</span><span class="sxs-lookup"><span data-stu-id="c979e-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c979e-167">共有遷移できますも作成することから、遷移デザイナー内をクリックして**共有トリガー遷移の追加**から目的のターゲットの状態をクリックして、遷移デザイナーの下部にある、 **接続に使用可能な状態**ドロップダウンします。</span><span class="sxs-lookup"><span data-stu-id="c979e-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c979e-168">遷移の <xref:System.Activities.Statements.Transition.Condition%2A> が `false` と評価された場合 (またはトリガーを共有する遷移すべての状態が `false` と評価された場合)、遷移は行われず、その状態からのすべての遷移のすべてのトリガーが再スケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="c979e-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="c979e-169">このチュートリアルでは、条件の構成方法 (推定値が正しいか間違っているかを判断する特定のアクションが用意されています) により、この状況は発生しません。</span><span class="sxs-lookup"><span data-stu-id="c979e-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="c979e-170">ダブルクリックして、 **Guess Incorrect**展開ワークフロー デザイナーで遷移します。</span><span class="sxs-lookup"><span data-stu-id="c979e-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="c979e-171">注意してください、**トリガー**は既に同じに設定**ReadInt**アクティビティで使用されていた、 **Guess Correct**遷移します。</span><span class="sxs-lookup"><span data-stu-id="c979e-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="c979e-172">次の式を入力、**条件**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="c979e-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="c979e-173">ドラッグ、**場合**からアクティビティ、**制御フロー**のセクションで、**ツールボックス**内にドロップし、**アクション**遷移のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="c979e-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="c979e-174">次の式を入力、**場合**アクティビティの**条件**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="c979e-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="c979e-175">2 つをドラッグして**WriteLine**からアクティビティを**プリミティブ**のセクション、**ツールボックス**が 1 つになるようにドロップして、**し**のセクション**場合**、もう 1 つでは、 **Else**セクションです。</span><span class="sxs-lookup"><span data-stu-id="c979e-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="c979e-176">クリックして、 **WriteLine**内のアクティビティ、**し**して選択し、セクションし、次の式を入力、**テキスト**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="c979e-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="c979e-177">クリックして、 **WriteLine**内のアクティビティ、 **Else**して選択し、セクションし、次の式を入力、**テキスト**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="c979e-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="c979e-178">全体的なに戻る をクリックしてステート マシン ビュー、ワークフロー デザイナー **StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。</span><span class="sxs-lookup"><span data-stu-id="c979e-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="c979e-179">次の例は完成したワークフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="c979e-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="c979e-180">![完成したステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="c979e-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="c979e-181">ワークフローをビルドするには</span><span class="sxs-lookup"><span data-stu-id="c979e-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="c979e-182">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c979e-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="c979e-183">ワークフローを実行する方法については、次のトピックをご覧ください。[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)です。</span><span class="sxs-lookup"><span data-stu-id="c979e-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="c979e-184">既に完了している場合、[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)ステップのワークフローとは異なるスタイルと共に、この手順で、ステート マシン ワークフローを使用して実行してに進んで、[アプリケーションをビルドして実行](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)のセクション[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)です。</span><span class="sxs-lookup"><span data-stu-id="c979e-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c979e-185">参照</span><span class="sxs-lookup"><span data-stu-id="c979e-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="c979e-186">Windows Workflow Foundation プログラミング</span><span class="sxs-lookup"><span data-stu-id="c979e-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="c979e-187">ワークフローの設計</span><span class="sxs-lookup"><span data-stu-id="c979e-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="c979e-188">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="c979e-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="c979e-189">アクティビティを作成する方法</span><span class="sxs-lookup"><span data-stu-id="c979e-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="c979e-190">ワークフローを実行する方法</span><span class="sxs-lookup"><span data-stu-id="c979e-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
