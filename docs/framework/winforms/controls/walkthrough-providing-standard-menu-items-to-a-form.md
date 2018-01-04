---
title: "チュートリアル : 標準メニュー項目をフォームに用意する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f1b976a0b5e0962cae155f380b17737077c5353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="bef1c-102">チュートリアル : 標準メニュー項目をフォームに用意する</span><span class="sxs-lookup"><span data-stu-id="bef1c-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="bef1c-103">フォームの標準のメニューを <xref:System.Windows.Forms.MenuStrip> コントロールに提供できます。</span><span class="sxs-lookup"><span data-stu-id="bef1c-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="bef1c-104">このチュートリアルを使用する方法を示します、<xref:System.Windows.Forms.MenuStrip>標準メニューを作成するコントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="bef1c-105">フォームは、ユーザーがメニュー項目を選択したときにも応答します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="bef1c-106">次のタスクは、このチュートリアルで例を示します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="bef1c-107">Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="bef1c-108">標準メニューを作成します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="bef1c-109">作成する、<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="bef1c-110">メニュー項目の選択を処理しています。</span><span class="sxs-lookup"><span data-stu-id="bef1c-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="bef1c-111">標準メニューにメニュー項目の選択を表示するフォームが完了したら、<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="bef1c-112">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: フォームに標準のメニュー項目の提供](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef1c-113">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bef1c-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bef1c-114">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bef1c-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bef1c-115">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bef1c-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bef1c-116">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bef1c-116">Prerequisites</span></span>  
 <span data-ttu-id="bef1c-117">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bef1c-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="bef1c-118">作成し、コンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセス許可を[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="bef1c-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="bef1c-119">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="bef1c-119">Creating the Project</span></span>  
 <span data-ttu-id="bef1c-120">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="bef1c-121">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="bef1c-121">To create the project</span></span>  
  
1.  <span data-ttu-id="bef1c-122">いう Windows アプリケーション プロジェクトを作成する**StandardMenuForm**です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-122">Create a Windows application project called **StandardMenuForm**.</span></span>  
  
     <span data-ttu-id="bef1c-123">詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bef1c-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="bef1c-124">Windows フォーム デザイナーでフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-124">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="bef1c-125">標準メニューを作成します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-125">Creating a Standard Menu</span></span>  
 <span data-ttu-id="bef1c-126">Windows フォーム デザイナーが自動的に設定できる、<xref:System.Windows.Forms.MenuStrip>標準メニュー項目を含むコントロールです。</span><span class="sxs-lookup"><span data-stu-id="bef1c-126">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="bef1c-127">標準メニューを作成するには</span><span class="sxs-lookup"><span data-stu-id="bef1c-127">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="bef1c-128">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="bef1c-128">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="bef1c-129">クリックして、<xref:System.Windows.Forms.MenuStrip>コントロールのスマート タグ グリフ (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) を選択して**標準項目の挿入**です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-129">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="bef1c-130"><xref:System.Windows.Forms.MenuStrip>標準メニュー項目コントロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bef1c-130">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="bef1c-131">クリックして、**ファイル**メニュー項目をその既定のメニュー項目と対応するアイコンを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bef1c-131">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="bef1c-132">StatusStrip コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="bef1c-132">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="bef1c-133">使用して、<xref:System.Windows.Forms.StatusStrip>して Windows フォーム アプリケーションの状態を表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-133">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="bef1c-134">現在の例では、ユーザーによって選択されたメニュー項目が表示されます、<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-134">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="bef1c-135">StatusStrip コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="bef1c-135">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="bef1c-136">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.StatusStrip>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="bef1c-136">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="bef1c-137"><xref:System.Windows.Forms.StatusStrip>コントロールが自動的に、フォームの下部にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="bef1c-137">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="bef1c-138">クリックして、<xref:System.Windows.Forms.StatusStrip>コントロールのドロップダウン ボタンをクリックし、選択**StatusLabel**を追加する、<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールを<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-138">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="bef1c-139">処理の項目の選択</span><span class="sxs-lookup"><span data-stu-id="bef1c-139">Handling Item Selection</span></span>  
 <span data-ttu-id="bef1c-140">処理、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント、ユーザーがメニュー項目を選択するときに応答します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-140">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="bef1c-141">項目の選択を処理するには</span><span class="sxs-lookup"><span data-stu-id="bef1c-141">To handle item selection</span></span>  
  
1.  <span data-ttu-id="bef1c-142">クリックして、**ファイル**作成で作成したメニュー項目に標準メニュー セクションです。</span><span class="sxs-lookup"><span data-stu-id="bef1c-142">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="bef1c-143">**プロパティ**ウィンドウで、をクリックして**イベント**です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-143">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="bef1c-144">ダブルクリックして、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント。</span><span class="sxs-lookup"><span data-stu-id="bef1c-144">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="bef1c-145">Windows フォーム デザイナーでのイベント ハンドラーが生成されます、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント。</span><span class="sxs-lookup"><span data-stu-id="bef1c-145">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="bef1c-146">イベント ハンドラーに次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-146">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="bef1c-147">挿入、`UpdateStatus`ユーティリティ メソッドの定義、フォームにします。</span><span class="sxs-lookup"><span data-stu-id="bef1c-147">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="bef1c-148">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="bef1c-148">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="bef1c-149">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="bef1c-149">To test your form</span></span>  
  
1.  <span data-ttu-id="bef1c-150">F5 キーを押してをコンパイルして、フォームを実行します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-150">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="bef1c-151">クリックして、**ファイル**メニュー項目、メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="bef1c-151">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="bef1c-152">**ファイル**] メニューの [選択項目のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bef1c-152">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="bef1c-153"><xref:System.Windows.Forms.StatusStrip>コントロールには、選択した項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bef1c-153">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="bef1c-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="bef1c-154">Next Steps</span></span>  
 <span data-ttu-id="bef1c-155">このチュートリアルでは、標準メニューを備えたフォームを作成しました。</span><span class="sxs-lookup"><span data-stu-id="bef1c-155">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="bef1c-156">使用することができます、<xref:System.Windows.Forms.ToolStrip>ファミリの他のさまざまな目的のコントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-156">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="bef1c-157">コントロールのショートカット メニューを作成する<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-157">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="bef1c-158">詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-158">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="bef1c-159">ドッキングとマルチ ドキュメント インターフェイス (MDI) フォームを作成する<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bef1c-159">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="bef1c-160">詳細については、次を参照してください。[チュートリアル: メニューのマージと ToolStrip コントロールを MDI フォームを作成する](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-160">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="bef1c-161">与える、<xref:System.Windows.Forms.ToolStrip>プロフェッショナルな外観を制御します。</span><span class="sxs-lookup"><span data-stu-id="bef1c-161">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="bef1c-162">詳細については、次を参照してください。[する方法: アプリケーションの ToolStrip レンダラーを設定](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="bef1c-162">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef1c-163">参照</span><span class="sxs-lookup"><span data-stu-id="bef1c-163">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="bef1c-164">MenuStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="bef1c-164">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
