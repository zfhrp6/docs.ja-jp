---
title: フローチャート ワークフローを作成する方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: c483a79a234d175fca63f27b4303b3f087c84e59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519338"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="2d4a3-102">フローチャート ワークフローを作成する方法</span><span class="sxs-lookup"><span data-stu-id="2d4a3-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="2d4a3-103">ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="2d4a3-104">など、両方の組み込みのアクティビティを使用するワークフローを作成する手順をこのトピックの内容、<xref:System.Activities.Statements.Flowchart>アクティビティ、およびカスタム アクティビティを以前から[する方法: アクティビティを作成](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="2d4a3-105">このワークフローは、数値推測ゲームをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d4a3-106">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="2d4a3-107">このトピックの内容を完了する必要があります最初に完了する[する方法: アクティビティを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d4a3-108">チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="2d4a3-109">ワークフローを作成するには</span><span class="sxs-lookup"><span data-stu-id="2d4a3-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="2d4a3-110">右クリック**NumberGuessWorkflowActivities**で**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の**します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="2d4a3-111">**インストール**、**共通項目**ノードで、選択**ワークフロー**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="2d4a3-112">選択**アクティビティ**から、**ワークフロー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="2d4a3-113">型`FlowchartNumberGuessWorkflow`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="2d4a3-114">ドラッグ、**フローチャート**からアクティビティを**フローチャート**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**のラベルをワークフロー デザイン サーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="2d4a3-115">ワークフロー変数および引数を作成するには</span><span class="sxs-lookup"><span data-stu-id="2d4a3-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="2d4a3-116">ダブルクリックして**FlowchartNumberGuessWorkflow.xaml**で**ソリューション エクスプ ローラー**をまだ表示されていない場合、デザイナーでワークフローを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="2d4a3-117">をクリックして**引数**を表示するワークフロー デザイナーの左下横で、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="2d4a3-118">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="2d4a3-119">型`MaxNumber`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、 **Int32** から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="2d4a3-120">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="2d4a3-121">型`Turns`に、**名前**、新しく追加した下にあるボックス`MaxNumber`引数で、**アウト**から、**方向**selectドロップダウンリスト**Int32**から、**引数の型**ドロップダウン リストとし、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="2d4a3-122">をクリックして**引数**を閉じる、アクティビティ デザイナーの左下横で、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="2d4a3-123">をクリックして**変数**を表示するワークフロー デザイナーの左下横で、**変数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="2d4a3-124">をクリックして**変数を作成**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="2d4a3-125">ない場合は**変数の作成**ボックスが表示されたら、をクリックして、<xref:System.Activities.Statements.Flowchart>それを選択するには、ワークフロー デザイナー画面上のアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="2d4a3-126">型`Guess`に、**名前**ボックスで、 **Int32**から、**変数型**ドロップダウン リスト、および、変数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="2d4a3-127">をクリックして**変数を作成**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="2d4a3-128">型`Target`に、**名前**ボックスで、 **Int32**から、**変数型**ドロップダウン リスト、および、変数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="2d4a3-129">をクリックして**変数**を閉じる、アクティビティ デザイナーの左下横で、**変数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="2d4a3-130">ワークフロー アクティビティを追加するには</span><span class="sxs-lookup"><span data-stu-id="2d4a3-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="2d4a3-131">ドラッグ、**割り当てる**からアクティビティを**プリミティブ**のセクションで、**ツールボックス**上に置きます、**開始**の上部にあるノード、フローチャート。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="2d4a3-132">ときに、**割り当てる**アクティビティが、**開始**ノード、囲む 3 つの三角形が表示されます、**開始**ノード。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="2d4a3-133">削除、**割り当てる**すぐ下にある三角形でのアクティビティ、**開始**ノード。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="2d4a3-134">これは、2 つの項目を一緒にリンクし、指定、**割り当てる**アクティビティがフローチャート内の最初のアクティビティとして。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2d4a3-135">アクティビティは、開始ノードに手動でリンクすることにより、ワークフローの開始アクティビティとして指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="2d4a3-136">これを行うには、マウス ポインター、**開始**ノード上にマウスがときに表示される四角形の 1 つをクリックして、**開始**ノード、およびドラッグして、接続して、目的のアクティビティに線の 1 つにドロップ表示される四角形。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="2d4a3-137">指定することも、アクティビティを it を右クリックし、選択の開始アクティビティとして**開始ノードとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-137">You can also designate and activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="2d4a3-138">型`Target`に、**に**ボックスおよびに次の式、 **c# 式を入力**または**VB の式を入力**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="2d4a3-139">場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="2d4a3-140">ドラッグ、**プロンプト**からアクティビティを**NumberGuessWorkflowActivities**のセクションで、**ツールボックス**、下にドロップして、**割り当てる**アクティビティ前のステップ、および接続、**プロンプト**アクティビティを**割り当てる**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="2d4a3-141">2 つのアクティビティを接続する方法は 3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="2d4a3-142">最初の方法がドロップするときに接続するには、**プロンプト**ワークフローのアクティビティをします。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="2d4a3-143">ドラッグする、**プロンプト**アクティビティをワークフロー上にマウス ポインター、**割り当てる**アクティビティのときに表示される 4 つの三角形の 1 つにドロップし、**プロンプト**アクティビティが、**割り当てる**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="2d4a3-144">2 番目の方法は、削除する、**プロンプト**アクティビティ、ワークフローの希望する位置。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="2d4a3-145">次に、マウス ポインター、**割り当てる**アクティビティと下に表示される四角形の 1 つドラッグ、**プロンプト**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="2d4a3-146">線を接続するように、マウスをドラッグ、**割り当てる**アクティビティの四角形のいずれかに接続する、**プロンプト**アクティビティ、およびマウス ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="2d4a3-147">3 番目の方法にドラッグすることではなく点を除いて、最初の方法とよく似ています、**プロンプト**からアクティビティを**ツールボックス**、ワークフロー デザイン サーフェイス上の場所からドラッグして、上にマウスポインター**割り当てる**アクティビティ、および表示される三角形の 1 つにドロップします。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="2d4a3-148">**プロパティ ウィンドウ**の**プロンプト**アクティビティで、「`"EnterGuess"`に引用符を含む、 **BookmarkName**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="2d4a3-149">型`Guess`に、**結果**プロパティの値のボックスとに次の式を入力、**テキスト**プロパティ ボックス。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="2d4a3-150">場合、**プロパティ ウィンドウ**が表示されていない select**プロパティ ウィンドウ**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="2d4a3-151">ドラッグ、**割り当てる**からアクティビティを**プリミティブ**のセクションで、**ツールボックス**下に、前の手順で説明する方法のいずれかを使用し接続**プロンプト**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="2d4a3-152">型`Turns`に、**に**ボックスおよび`Turns + 1`に、 **c# 式を入力**または**VB の式を入力**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="2d4a3-153">ドラッグ、 **FlowDecision**から、**フローチャート**のセクションで、**ツールボックス**下に接続し、**割り当てる**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="2d4a3-154">**プロパティ ウィンドウ**、次の式を入力、**条件**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="2d4a3-155">別のドラッグ**FlowDecision**からアクティビティを**ツールボックス**つ目の下にドロップします。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="2d4a3-156">というラベルが付いた四角形からドラッグして 2 つのアクティビティを接続**False**上**FlowDecision** 、2 つ目の上部にある四角形をアクティビティ**FlowDecision**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="2d4a3-157">表示されない場合、 **True**と**False**ラベル、 **FlowDecision**、マウス ポインター、 **FlowDecision**です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="2d4a3-158">2 つ目のクリックして**FlowDecision**アクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="2d4a3-159">**プロパティ ウィンドウ**、次の式を入力、**条件**プロパティ値ボックスです。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="2d4a3-160">2 つをドラッグして**WriteLine**からアクティビティを**プリミティブ**のセクションで、**ツールボックス**ようにサイド バイ サイドで 2 つの下にドロップして**FlowDecision**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="2d4a3-161">接続、 **True**下部のアクション**FlowDecision**を最も左アクティビティ**WriteLine**アクティビティ、および**False**アクションを右端**WriteLine**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="2d4a3-162">最も左クリックして**WriteLine**アクティビティを選択し、次の式を入力、**テキスト**プロパティ値ボックスに、**プロパティ ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="2d4a3-163">接続、 **WriteLine**の左側に、**プロンプト**上にあるアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="2d4a3-164">最も右クリックして**WriteLine**アクティビティを選択し、次の式を入力、**テキスト**プロパティ値ボックスに、**プロパティ ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="2d4a3-165">接続、 **WriteLine**の右側にあるアクティビティ、**プロンプト**その上アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="2d4a3-166">次の例は完成したワークフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="2d4a3-167">![Windows Workflow Foundation の完了](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="2d4a3-167">![Completed Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="2d4a3-168">ワークフローをビルドするには</span><span class="sxs-lookup"><span data-stu-id="2d4a3-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="2d4a3-169">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="2d4a3-170">ワークフローを実行する方法については、次のトピックをご覧ください。[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="2d4a3-171">既に完了している場合、[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)ステップのワークフローとは異なるスタイルと共に、この手順でフローチャート ワークフローを使用して実行してに進んで、[アプリケーションをビルドして実行](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)のセクション[する方法: ワークフローを実行する](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d4a3-171">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4a3-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d4a3-172">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="2d4a3-173">Windows Workflow Foundation プログラミング</span><span class="sxs-lookup"><span data-stu-id="2d4a3-173">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="2d4a3-174">ワークフローの設計</span><span class="sxs-lookup"><span data-stu-id="2d4a3-174">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="2d4a3-175">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="2d4a3-175">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="2d4a3-176">アクティビティを作成する方法</span><span class="sxs-lookup"><span data-stu-id="2d4a3-176">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="2d4a3-177">ワークフローを実行する方法</span><span class="sxs-lookup"><span data-stu-id="2d4a3-177">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
