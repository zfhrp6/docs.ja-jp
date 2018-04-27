---
title: アクティビティを作成する方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0d0d48d1e78efb3484f521958edf22d97ca8053d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="97621-102">アクティビティを作成する方法</span><span class="sxs-lookup"><span data-stu-id="97621-102">How to: Create an Activity</span></span>
<span data-ttu-id="97621-103">アクティビティは [!INCLUDE[wf1](../../../includes/wf1-md.md)] の動作の中心的な単位です。</span><span class="sxs-lookup"><span data-stu-id="97621-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="97621-104">アクティビティの実行ロジックはマネージ コードで実装できます。または他のアクティビティを使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="97621-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="97621-105">このトピックでは、2 つのアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97621-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="97621-106">最初のアクティビティは、コードを使用してその実行ロジックを実装する単純なアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="97621-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="97621-107">2 番目のアクティビティの実装は他のアクティビティを使用して定義されています。</span><span class="sxs-lookup"><span data-stu-id="97621-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="97621-108">これらのアクティビティは、チュートリアルの次の手順で使用します。</span><span class="sxs-lookup"><span data-stu-id="97621-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97621-109">チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97621-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="97621-110">アクティビティ ライブラリ プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="97621-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="97621-111">開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選択**新規**、**プロジェクト**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="97621-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="97621-112">展開、**その他のプロジェクトの種類**内のノード、**インストール済み**、**テンプレート**選択**Visual Studio ソリューション**です。</span><span class="sxs-lookup"><span data-stu-id="97621-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="97621-113">選択**空のソリューション**から、 **Visual Studio ソリューション** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="97621-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="97621-114">.NET Framework バージョンのドロップダウン リストで **[.NET Framework 4.5]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="97621-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="97621-115">型`WF45GettingStartedTutorial`で、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="97621-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="97621-116">右クリック**WF45GettingStartedTutorial**で**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="97621-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="97621-117">**ソリューション エクスプローラー** ウィンドウが表示されない場合は、 **[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97621-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="97621-118">**[インストール済み]** ノードで、 **[Visual C#]**、 **[ワークフロー]** (または **[Visual Basic]**、 **[ワークフロー]**) の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="97621-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="97621-119">いることを確認 **.NET Framework 4.5**でが選択されている、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]バージョンのドロップダウン リスト。</span><span class="sxs-lookup"><span data-stu-id="97621-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="97621-120">選択**アクティビティ ライブラリ**から、**ワークフロー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="97621-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="97621-121">型`NumberGuessWorkflowActivities`で、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="97621-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97621-122">Visual Studio で第一言語として設定されているプログラミング言語に応じて、 **[インストール済み]** ノードの **[他の言語]** ノードの下に、 **[Visual C#]** ノードまたは **[Visual Basic]** ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="97621-122">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="97621-123">右クリック**Activity1.xaml**で**ソリューション エクスプ ローラー**選択**削除**です。</span><span class="sxs-lookup"><span data-stu-id="97621-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="97621-124">**[OK]** をクリックして確定します。</span><span class="sxs-lookup"><span data-stu-id="97621-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="97621-125">ReadInt アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="97621-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="97621-126">選択**新しい項目の追加**から、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="97621-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="97621-127">**インストール**、**共通項目**ノードで、選択**ワークフロー**です。</span><span class="sxs-lookup"><span data-stu-id="97621-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="97621-128">選択**コード アクティビティ**から、**ワークフロー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="97621-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="97621-129">型`ReadInt`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="97621-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="97621-130">既存の `ReadInt` 定義を次の定義に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="97621-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="97621-131">`ReadInt` アクティビティは、コード アクティビティ テンプレートの既定値である <xref:System.Activities.NativeActivity%601> ではなく <xref:System.Activities.CodeActivity> から派生します。</span><span class="sxs-lookup"><span data-stu-id="97621-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="97621-132"><xref:System.Activities.CodeActivity%601> は、<xref:System.Activities.Activity%601.Result%2A> 引数を介して公開される 1 つの結果がアクティビティによって提供される場合に使用できますが、<xref:System.Activities.CodeActivity%601> ではブックマークの使用がサポートされていないため、<xref:System.Activities.NativeActivity%601> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="97621-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="97621-133">Prompt アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="97621-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="97621-134">Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="97621-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="97621-135">プロジェクトをビルドすると、このプロジェクトの `ReadInt` アクティビティを使用して、この手順からカスタム アクティビティをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="97621-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="97621-136">選択**新しい項目の追加**から、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="97621-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="97621-137">**インストール**、**共通項目**ノードで、選択**ワークフロー**です。</span><span class="sxs-lookup"><span data-stu-id="97621-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="97621-138">選択**アクティビティ**から、**ワークフロー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="97621-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="97621-139">型`Prompt`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="97621-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="97621-140">ダブルクリックして**Prompt.xaml**で**ソリューション エクスプ ローラー**をまだ表示されていない場合、デザイナーで表示します。</span><span class="sxs-lookup"><span data-stu-id="97621-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="97621-141">をクリックして**引数**を表示するアクティビティ デザイナーの左下横で、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="97621-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="97621-142">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="97621-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="97621-143">型`BookmarkName`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**文字列**から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="97621-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="97621-144">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="97621-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="97621-145">型`Result`に、**名前**、新たに追加の下にあるボックスを`BookmarkName`引数で、**アウト**から、**方向**ドロップダウン リストで、**Int32**から、**引数の型**ドロップダウン リストとし、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="97621-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="97621-146">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="97621-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="97621-147">型`Text`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**文字列**から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="97621-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="97621-148">これら 3 つの引数は、次の手順で、<xref:System.Activities.Statements.WriteLine> アクティビティに追加される `ReadInt` アクティビティと `Prompt` アクティビティの対応する引数にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="97621-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="97621-149">をクリックして**引数**を閉じる、アクティビティ デザイナーの左下横で、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="97621-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="97621-150">ドラッグ、**シーケンス**からアクティビティを**制御フロー**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**のラベル、**プロンプト**アクティビティ デザイナー。</span><span class="sxs-lookup"><span data-stu-id="97621-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="97621-151">場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="97621-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="97621-152">ドラッグ、 **WriteLine**からアクティビティを**プリミティブ**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**のラベル、**シーケンス**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="97621-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="97621-153">バインド、**テキスト**の引数、 **WriteLine**アクティビティを**テキスト**の引数、**プロンプト**」と入力してアクティビティ`Text`**c# 式を入力**または**VB の式を入力**ボックスに、**プロパティ**キー 2 回のウィンドウとし、TAB キーを押します。</span><span class="sxs-lookup"><span data-stu-id="97621-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="97621-154">これで、IntelliSense リスト メンバー ウィンドウを閉じ、プロパティから選択を外してプロパティ値を保存します。</span><span class="sxs-lookup"><span data-stu-id="97621-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="97621-155">このプロパティは、」と入力して設定することもできます`Text`に、 **c# 式を入力**または**VB の式を入力**アクティビティ自体のボックスです。</span><span class="sxs-lookup"><span data-stu-id="97621-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="97621-156">場合、**プロパティ ウィンドウ**が表示されていない select**プロパティ ウィンドウ**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="97621-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="97621-157">ドラッグ、 **ReadInt**からアクティビティを**NumberGuessWorkflowActivities**のセクションで、**ツールボックス**内にドロップし、**シーケンス**アクティビティの後になるように、 **WriteLine**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="97621-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="97621-158">バインド、 **BookmarkName**の引数、 **ReadInt**アクティビティを**BookmarkName**の引数、**プロンプト** 」と入力してアクティビティ`BookmarkName`に、 **VB の式を入力**の右側のボックスに、 **BookmarkName**の引数、**プロパティ ウィンドウ**、TAB キーを押します 2IntelliSense リスト メンバー ウィンドウを閉じて、プロパティを保存する時間します。</span><span class="sxs-lookup"><span data-stu-id="97621-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="97621-159">バインド、**結果**の引数、 **ReadInt**アクティビティを**結果**の引数、**プロンプト**」と入力してアクティビティ`Result`**VB の式を入力**の右側のボックスに、**結果**の引数、**プロパティ ウィンドウ**とし、TAB キーを 2 回押します。</span><span class="sxs-lookup"><span data-stu-id="97621-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="97621-160">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="97621-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="97621-161">これらのアクティビティを使用してワークフローを作成する方法については、チュートリアルでは、次の手順を参照してください[する方法: ワークフローを作成](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)です。</span><span class="sxs-lookup"><span data-stu-id="97621-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97621-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="97621-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="97621-163">カスタム アクティビティの設計と実装</span><span class="sxs-lookup"><span data-stu-id="97621-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="97621-164">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="97621-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="97621-165">ワークフローを作成する方法</span><span class="sxs-lookup"><span data-stu-id="97621-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="97621-166">カスタム アクティビティ デザイナーでの ExpressionTextBox の使用</span><span class="sxs-lookup"><span data-stu-id="97621-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
