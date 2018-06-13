---
title: 'チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 124f822aeab25f49cea0ad542497a91a9e2030d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541620"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="36dac-102">チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="36dac-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="36dac-103"><xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、マルチ ドキュメント インターフェイス (MDI) アプリケーションをサポートし、<xref:System.Windows.Forms.MenuStrip> コントロールはメニューの結合をサポートします。</span><span class="sxs-lookup"><span data-stu-id="36dac-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="36dac-104">MDI フォームは、<xref:System.Windows.Forms.ToolStrip> コントロールもサポートします。</span><span class="sxs-lookup"><span data-stu-id="36dac-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="36dac-105">このチュートリアルを使用する方法を示します<xref:System.Windows.Forms.ToolStripPanel>を MDI フォームでコントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="36dac-106">フォームは、子メニューをマージするメニューもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="36dac-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="36dac-107">次のタスクは、このチュートリアルで例を示します。</span><span class="sxs-lookup"><span data-stu-id="36dac-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="36dac-108">Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="36dac-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="36dac-109">フォームのメイン メニューを作成します。</span><span class="sxs-lookup"><span data-stu-id="36dac-109">Creating the main menu for your form.</span></span> <span data-ttu-id="36dac-110">メニューの実際の名前が異なります。</span><span class="sxs-lookup"><span data-stu-id="36dac-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="36dac-111">追加する、<xref:System.Windows.Forms.ToolStripPanel>コントロールを**ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="36dac-112">子フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="36dac-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="36dac-113">配置<xref:System.Windows.Forms.ToolStripPanel>z オーダーでコントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="36dac-114">メニューのマージおよび移動をサポートする MDI フォームが完了したら、<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="36dac-115">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: メニューのマージと ToolStrip コントロールを MDI フォームを作成](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="36dac-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36dac-116">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="36dac-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="36dac-117">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36dac-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="36dac-118">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36dac-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="36dac-119">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="36dac-119">Prerequisites</span></span>  
 <span data-ttu-id="36dac-120">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36dac-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="36dac-121">作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="36dac-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="36dac-122">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="36dac-122">Creating the Project</span></span>  
 <span data-ttu-id="36dac-123">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="36dac-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="36dac-124">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="36dac-124">To create the project</span></span>  
  
1.  <span data-ttu-id="36dac-125">いう Windows アプリケーション プロジェクトを作成する**mdi フォーム**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-125">Create a Windows Application project called **MdiForm**.</span></span>  
  
     <span data-ttu-id="36dac-126">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36dac-126">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="36dac-127">Windows フォーム デザイナーでフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="36dac-127">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="36dac-128">[プロパティ] ウィンドウ内の値を設定、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>に`true`です。</span><span class="sxs-lookup"><span data-stu-id="36dac-128">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="36dac-129">メイン メニューの作成</span><span class="sxs-lookup"><span data-stu-id="36dac-129">Creating the Main Menu</span></span>  
 <span data-ttu-id="36dac-130">親 MDI フォームには、メイン メニューが含まれています。</span><span class="sxs-lookup"><span data-stu-id="36dac-130">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="36dac-131">メイン メニューがという名前の項目 1 つのメニュー**ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="36dac-131">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="36dac-132">**ウィンドウ**メニュー項目の子フォームを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="36dac-132">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="36dac-133">子フォームのメニュー項目は、メイン メニューにマージされます。</span><span class="sxs-lookup"><span data-stu-id="36dac-133">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="36dac-134">メイン メニューを作成するには</span><span class="sxs-lookup"><span data-stu-id="36dac-134">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="36dac-135">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="36dac-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="36dac-136">追加、<xref:System.Windows.Forms.ToolStripMenuItem>を<xref:System.Windows.Forms.MenuStrip>を制御し、名前を付けます**ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="36dac-136">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="36dac-137"><xref:System.Windows.Forms.MenuStrip> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="36dac-137">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="36dac-138">[プロパティ] ウィンドウ内の値を設定、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティを`ToolStripMenuItem1`です。</span><span class="sxs-lookup"><span data-stu-id="36dac-138">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="36dac-139">サブ項目を追加、**ウィンドウ**メニュー項目と、名前、サブアイテム**新規**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-139">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="36dac-140">[プロパティ] ウィンドウでをクリックして**イベント**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-140">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="36dac-141">ダブルクリックして、<xref:System.Windows.Forms.ToolStripItem.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="36dac-141">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="36dac-142">Windows フォーム デザイナーでのイベント ハンドラーが生成されます、<xref:System.Windows.Forms.ToolStripItem.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="36dac-142">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="36dac-143">イベント ハンドラーに次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="36dac-143">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="36dac-144">ToolStripPanel コントロールをツールボックスに追加します。</span><span class="sxs-lookup"><span data-stu-id="36dac-144">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="36dac-145">使用すると<xref:System.Windows.Forms.MenuStrip>する必要があります、MDI フォームでコントロール、<xref:System.Windows.Forms.ToolStripPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-145">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="36dac-146">追加する必要があります、<xref:System.Windows.Forms.ToolStripPanel>コントロールを**ツールボックス**Windows フォーム デザイナーで、MDI フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="36dac-146">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="36dac-147">ToolStripPanel コントロールをツールボックスに追加するには</span><span class="sxs-lookup"><span data-stu-id="36dac-147">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="36dac-148">開く、**ツールボックス**、をクリックし、**すべての Windows フォーム**利用可能な Windows フォーム コントロールを表示するタブです。</span><span class="sxs-lookup"><span data-stu-id="36dac-148">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="36dac-149">開くには、ショートカット メニューを右クリックし **アイテムの選択**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-149">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="36dac-150">**ツールボックス アイテムの選択**ダイアログ ボックスで、下へスクロールして、**名前**列が見つかるまで**ToolStripPanel**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-150">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="36dac-151">チェック ボックスをオンに**ToolStripPanel**、順にクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-151">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="36dac-152"><xref:System.Windows.Forms.ToolStripPanel>コントロールに表示され、**ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-152">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="36dac-153">子フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="36dac-153">Creating a Child Form</span></span>  
 <span data-ttu-id="36dac-154">この手順をそれ自体を持つ 1 つの子フォーム クラスを定義します<xref:System.Windows.Forms.MenuStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-154">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="36dac-155">このフォームのメニュー項目は、親フォームのマージされます。</span><span class="sxs-lookup"><span data-stu-id="36dac-155">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="36dac-156">子フォームを定義するには</span><span class="sxs-lookup"><span data-stu-id="36dac-156">To define a child form</span></span>  
  
1.  <span data-ttu-id="36dac-157">という名前の新しいフォームを追加`ChildForm`をプロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="36dac-157">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="36dac-158">詳細については、次を参照してください。[する方法: Windows フォームをプロジェクトに追加](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1)です。</span><span class="sxs-lookup"><span data-stu-id="36dac-158">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="36dac-159">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>子フォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="36dac-159">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="36dac-160">クリックして、<xref:System.Windows.Forms.MenuStrip>コントロールのスマート タグ グリフ (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))、し、**アイテムの編集**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-160">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="36dac-161">**Items コレクション エディター**  ダイアログ ボックスで、追加、新しい<xref:System.Windows.Forms.ToolStripMenuItem>という**ChildMenuItem**子メニューをします。</span><span class="sxs-lookup"><span data-stu-id="36dac-161">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="36dac-162">詳細については、次を参照してください。 [ToolStrip Items コレクション エディター](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)です。</span><span class="sxs-lookup"><span data-stu-id="36dac-162">For more information, see [ToolStrip Items Collection Editor](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="36dac-163">フォームのテスト</span><span class="sxs-lookup"><span data-stu-id="36dac-163">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="36dac-164">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="36dac-164">To test your form</span></span>  
  
1.  <span data-ttu-id="36dac-165">F5 キーを押してをコンパイルして、フォームを実行します。</span><span class="sxs-lookup"><span data-stu-id="36dac-165">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="36dac-166">クリックして、**ウィンドウ**、メニューを開き、をクリックしてメニュー項目**新規**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-166">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="36dac-167">新しい子フォームは、フォームの MDI クライアント領域に作成されます。</span><span class="sxs-lookup"><span data-stu-id="36dac-167">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="36dac-168">子フォームのメニューは、メイン メニューに結合されます。</span><span class="sxs-lookup"><span data-stu-id="36dac-168">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="36dac-169">子フォームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36dac-169">Close the child form.</span></span>  
  
     <span data-ttu-id="36dac-170">子フォームのメニューは、メイン メニューから削除されます。</span><span class="sxs-lookup"><span data-stu-id="36dac-170">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="36dac-171">をクリックして**新規**何回か。</span><span class="sxs-lookup"><span data-stu-id="36dac-171">Click **New** several times.</span></span>  
  
     <span data-ttu-id="36dac-172">子フォームは自動的に、「、W**ウィンドウ**メニュー項目のため、<xref:System.Windows.Forms.MenuStrip>コントロールの<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="36dac-172">The child forms are automatically listed under the W**indow** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="36dac-173">ToolStrip のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="36dac-173">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="36dac-174">この手順では追加 4 <xref:System.Windows.Forms.ToolStrip> MDI 親フォームのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="36dac-174">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="36dac-175">各<xref:System.Windows.Forms.ToolStrip>内にコントロールを追加、<xref:System.Windows.Forms.ToolStripPanel>フォームの端にドッキングされているコントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-175">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="36dac-176">ToolStrip コントロールを MDI 親フォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="36dac-176">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="36dac-177">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ToolStripPanel>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="36dac-177">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="36dac-178"><xref:System.Windows.Forms.ToolStripPanel>コントロールを選択し、ダブルクリック、<xref:System.Windows.Forms.ToolStrip>内の制御、**ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-178">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="36dac-179">A<xref:System.Windows.Forms.ToolStrip>でコントロールが作成された、<xref:System.Windows.Forms.ToolStripPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-179">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="36dac-180"><xref:System.Windows.Forms.ToolStripPanel> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="36dac-180">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="36dac-181">[プロパティ] ウィンドウでのコントロールの値を変更<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Left>です。</span><span class="sxs-lookup"><span data-stu-id="36dac-181">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="36dac-182"><xref:System.Windows.Forms.ToolStripPanel>メイン メニューの下に、フォームの左側にドッキングを制御します。</span><span class="sxs-lookup"><span data-stu-id="36dac-182">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="36dac-183">MDI クライアント領域のサイズに合わせて、<xref:System.Windows.Forms.ToolStripPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-183">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="36dac-184">手順 1. ~ 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="36dac-184">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="36dac-185">新しいドッキング<xref:System.Windows.Forms.ToolStripPanel>フォームの上部を制御します。</span><span class="sxs-lookup"><span data-stu-id="36dac-185">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="36dac-186"><xref:System.Windows.Forms.ToolStripPanel>コントロールが、メイン メニューの下には、最初の右側にドッキングされている<xref:System.Windows.Forms.ToolStripPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-186">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="36dac-187">この手順は、正しく配置の z オーダーの重要度を示しています。<xref:System.Windows.Forms.ToolStripPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-187">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="36dac-188">2 つの手順 1. ~ 4. を繰り返します<xref:System.Windows.Forms.ToolStripPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-188">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="36dac-189">新しいドッキング<xref:System.Windows.Forms.ToolStripPanel>の権限と、フォームの一番下へのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="36dac-189">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="36dac-190">Z オーダーで ToolStripPanel コントロールの配置</span><span class="sxs-lookup"><span data-stu-id="36dac-190">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="36dac-191">位置、ドッキングされた<xref:System.Windows.Forms.ToolStripPanel>MDI フォーム上のコントロールを z オーダーでコントロールの位置によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="36dac-191">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="36dac-192">ドキュメント アウトライン ウィンドウでコントロールの z オーダーを簡単に配置できます。</span><span class="sxs-lookup"><span data-stu-id="36dac-192">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="36dac-193">Z オーダーで ToolStripPanel コントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="36dac-193">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="36dac-194">**ビュー** ] メニューのをクリックして**その他のウィンドウ**、クリックして **[ドキュメント アウトライン**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-194">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="36dac-195">配置、<xref:System.Windows.Forms.ToolStripPanel>前の手順からコントロールは非標準です。</span><span class="sxs-lookup"><span data-stu-id="36dac-195">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="36dac-196">これは、z オーダーが正しくないためです。</span><span class="sxs-lookup"><span data-stu-id="36dac-196">This is because the z-order is not correct.</span></span> <span data-ttu-id="36dac-197">ドキュメント アウトライン ウィンドウを使用すると、コントロールの z オーダーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="36dac-197">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="36dac-198">ドキュメント アウトライン ウィンドウで、次のように選択します。 **ToolStripPanel4**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-198">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="36dac-199">下向きの矢印ボタンをクリックするまで繰り返し、 **ToolStripPanel4**は一覧の下部にします。</span><span class="sxs-lookup"><span data-stu-id="36dac-199">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="36dac-200">**ToolStripPanel4**コントロールが他のコントロールの下に、フォームの下部にドッキングされています。</span><span class="sxs-lookup"><span data-stu-id="36dac-200">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="36dac-201">選択**ToolStripPanel2**です。</span><span class="sxs-lookup"><span data-stu-id="36dac-201">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="36dac-202">一覧で 3 番目にコントロールの位置を 1 回下向きの矢印ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36dac-202">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="36dac-203">**ToolStripPanel2**コントロールは、メイン メニューの下にあると、その他のコントロールの上、フォームの上部にドッキングされています。</span><span class="sxs-lookup"><span data-stu-id="36dac-203">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="36dac-204">さまざまなコントロール、 **ドキュメント アウトライン**ウィンドウし、z オーダーで別の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="36dac-204">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="36dac-205">Z オーダーのドッキングされたコントロールの配置への影響に注意してください。</span><span class="sxs-lookup"><span data-stu-id="36dac-205">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="36dac-206">CTRL + Z を使用してまたは**を元に戻す**上、**編集**変更を元に戻す] メニューの [します。</span><span class="sxs-lookup"><span data-stu-id="36dac-206">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="36dac-207">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="36dac-207">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="36dac-208">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="36dac-208">To test your form</span></span>  
  
1.  <span data-ttu-id="36dac-209">F5 キーを押してをコンパイルして、フォームを実行します。</span><span class="sxs-lookup"><span data-stu-id="36dac-209">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="36dac-210">ハンドルをクリックして、<xref:System.Windows.Forms.ToolStrip>を制御し、フォーム上の別の位置にコントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="36dac-210">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="36dac-211">ドラッグすることができます、<xref:System.Windows.Forms.ToolStrip>から 1 つのコントロール<xref:System.Windows.Forms.ToolStripPanel>を別のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="36dac-211">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36dac-212">次の手順</span><span class="sxs-lookup"><span data-stu-id="36dac-212">Next Steps</span></span>  
 <span data-ttu-id="36dac-213">このチュートリアルで MDI 親フォームを作成した<xref:System.Windows.Forms.ToolStrip>コントロールやメニューのマージします。</span><span class="sxs-lookup"><span data-stu-id="36dac-213">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="36dac-214">使用することができます、<xref:System.Windows.Forms.ToolStrip>ファミリの他のさまざまな目的のコントロール。</span><span class="sxs-lookup"><span data-stu-id="36dac-214">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="36dac-215">コントロールのショートカット メニューを作成する<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="36dac-215">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="36dac-216">詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="36dac-216">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="36dac-217">自動的に設定された標準のメニューで、フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="36dac-217">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="36dac-218">詳細については、次を参照してください。[チュートリアル: 標準メニュー項目をフォームに](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)です。</span><span class="sxs-lookup"><span data-stu-id="36dac-218">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="36dac-219">与える、<xref:System.Windows.Forms.ToolStrip>プロフェッショナルな外観を制御します。</span><span class="sxs-lookup"><span data-stu-id="36dac-219">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="36dac-220">詳細については、次を参照してください。[する方法: アプリケーションの ToolStrip レンダラーを設定](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="36dac-220">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36dac-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="36dac-221">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="36dac-222">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="36dac-222">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="36dac-223">方法: MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="36dac-223">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="36dac-224">方法: MDI ドロップダウン メニューに MenuStrip を挿入する</span><span class="sxs-lookup"><span data-stu-id="36dac-224">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="36dac-225">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="36dac-225">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
