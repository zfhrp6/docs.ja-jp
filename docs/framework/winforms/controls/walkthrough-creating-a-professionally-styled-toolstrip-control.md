---
title: "チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成"
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab9adb72a174da25298b6ea104b002914de0cc40
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="203f9-102">チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="203f9-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="203f9-103">アプリケーションを移すことができる<xref:System.Windows.Forms.ToolStrip>から派生した独自のクラスを記述して、プロフェッショナルな外観と動作を制御、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>型です。</span><span class="sxs-lookup"><span data-stu-id="203f9-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="203f9-104">このチュートリアルを使用する方法を示します<xref:System.Windows.Forms.ToolStrip>に似た複合コントロールを作成するコントロール、**ナビゲーション ウィンドウ**Microsoft® Outlook® によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="203f9-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="203f9-105">次のタスクは、このチュートリアルで例を示します。</span><span class="sxs-lookup"><span data-stu-id="203f9-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="203f9-106">Windows コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="203f9-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="203f9-107">StackView コントロールをデザインします。</span><span class="sxs-lookup"><span data-stu-id="203f9-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="203f9-108">カスタム レンダラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="203f9-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="203f9-109">完了したら、Microsoft Office® XP コントロールのプロフェッショナルな外観を持つカスタムのクライアントを再利用可能なコントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="203f9-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="203f9-110">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: プロフェッショナル スタイルの ToolStrip コントロールを作成](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="203f9-111">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="203f9-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="203f9-112">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="203f9-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="203f9-113">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="203f9-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="203f9-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="203f9-114">Prerequisites</span></span>  
 <span data-ttu-id="203f9-115">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="203f9-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="203f9-116">作成し、コンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセス許可を[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="203f9-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="203f9-117">Windows コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="203f9-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="203f9-118">最初の手順では、コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="203f9-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="203f9-119">コントロール ライブラリ プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="203f9-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="203f9-120">という名前の新しい Windows コントロール ライブラリ プロジェクトを作成する`StackViewLibrary`です。</span><span class="sxs-lookup"><span data-stu-id="203f9-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="203f9-121">**ソリューション エクスプ ローラー**、選択した言語に応じて"UserControl1.cs"または"UserControl1.vb"をという名前のソース ファイルを削除して、プロジェクトの既定のコントロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="203f9-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="203f9-122">詳細については、次を参照してください。 [NIB: 方法:: 削除、削除、および項目の除外](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="203f9-123">新しい<xref:System.Windows.Forms.UserControl>項目を**StackViewLibrary**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="203f9-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="203f9-124">新しいソース ファイルの基本の名前を付けます`StackView`です。</span><span class="sxs-lookup"><span data-stu-id="203f9-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="203f9-125">StackView コントロールのデザイン</span><span class="sxs-lookup"><span data-stu-id="203f9-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="203f9-126">`StackView`コントロールは、1 つの子による複合コントロール<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="203f9-127">複合コントロールの詳細については、次を参照してください。[カスタム コントロールの種類](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="203f9-128">StackView コントロールを設計するには</span><span class="sxs-lookup"><span data-stu-id="203f9-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="203f9-129">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ToolStrip>コントロールをデザイン画面にします。</span><span class="sxs-lookup"><span data-stu-id="203f9-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="203f9-130">**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolStrip>次の表に従ってコントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="203f9-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="203f9-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="203f9-131">Property</span></span>|<span data-ttu-id="203f9-132">値</span><span class="sxs-lookup"><span data-stu-id="203f9-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="203f9-133">name</span><span class="sxs-lookup"><span data-stu-id="203f9-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="203f9-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="203f9-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="203f9-135">ドッキング</span><span class="sxs-lookup"><span data-stu-id="203f9-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="203f9-136">フォント</span><span class="sxs-lookup"><span data-stu-id="203f9-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="203f9-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="203f9-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="203f9-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="203f9-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="203f9-139">[間隔]</span><span class="sxs-lookup"><span data-stu-id="203f9-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="203f9-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="203f9-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="203f9-141">Windows フォーム デザイナーでをクリックして、<xref:System.Windows.Forms.ToolStrip>コントロールの**追加**ボタンをクリックし、追加、<xref:System.Windows.Forms.ToolStripButton>を`stackStrip`コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="203f9-142">**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolStripButton>次の表に従ってコントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="203f9-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="203f9-143">プロパティ</span><span class="sxs-lookup"><span data-stu-id="203f9-143">Property</span></span>|<span data-ttu-id="203f9-144">値</span><span class="sxs-lookup"><span data-stu-id="203f9-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="203f9-145">name</span><span class="sxs-lookup"><span data-stu-id="203f9-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="203f9-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="203f9-146">CheckOnClick</span></span>|<span data-ttu-id="203f9-147">true</span><span class="sxs-lookup"><span data-stu-id="203f9-147">true</span></span>|  
    |<span data-ttu-id="203f9-148">CheckState</span><span class="sxs-lookup"><span data-stu-id="203f9-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="203f9-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="203f9-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="203f9-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="203f9-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="203f9-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="203f9-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="203f9-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="203f9-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="203f9-153">Margin</span><span class="sxs-lookup"><span data-stu-id="203f9-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="203f9-154">[間隔]</span><span class="sxs-lookup"><span data-stu-id="203f9-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="203f9-155">テキスト</span><span class="sxs-lookup"><span data-stu-id="203f9-155">Text</span></span>|<span data-ttu-id="203f9-156">**メール**</span><span class="sxs-lookup"><span data-stu-id="203f9-156">**Mail**</span></span>|  
    |<span data-ttu-id="203f9-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="203f9-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="203f9-158">複数の 3 つの手順 7.<xref:System.Windows.Forms.ToolStripButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="203f9-159">コントロールの名前を付けます`calendarStackButton`、 `contactsStackButton`、および`tasksStackButton`です。</span><span class="sxs-lookup"><span data-stu-id="203f9-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="203f9-160">値を設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを**カレンダー**、**連絡先**、および**タスク**、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="203f9-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="203f9-161">イベントの処理</span><span class="sxs-lookup"><span data-stu-id="203f9-161">Handling Events</span></span>  
 <span data-ttu-id="203f9-162">2 つのイベントは、重要な`StackView`コントロールが適切に動作します。</span><span class="sxs-lookup"><span data-stu-id="203f9-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="203f9-163">処理、<xref:System.Windows.Forms.UserControl.Load>コントロールを正しく配置するイベントです。</span><span class="sxs-lookup"><span data-stu-id="203f9-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="203f9-164">処理、<xref:System.Windows.Forms.ToolStripItem.Click>各イベント<xref:System.Windows.Forms.ToolStripButton>を与える、`StackView`のような状態の動作を制御、<xref:System.Windows.Forms.RadioButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="203f9-165">イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="203f9-165">To handle events</span></span>  
  
1.  <span data-ttu-id="203f9-166">Windows フォーム デザイナーで、選択、`StackView`コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="203f9-167">**プロパティ**ウィンドウで、をクリックして**イベント**です。</span><span class="sxs-lookup"><span data-stu-id="203f9-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="203f9-168">Load イベントをダブルクリックして、`StackView_Load`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="203f9-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="203f9-169">`StackView_Load` イベント ハンドラーで、次のコードをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="203f9-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="203f9-170">Windows フォーム デザイナーで、選択、`mailStackButton`コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="203f9-171">**プロパティ**ウィンドウで、をクリックして**イベント**です。</span><span class="sxs-lookup"><span data-stu-id="203f9-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="203f9-172">Click イベントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="203f9-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="203f9-173">Windows フォーム デザイナーで生成する、`mailStackButton_Click`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="203f9-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="203f9-174">名前を変更、`mailStackButton_Click`イベント ハンドラーを`stackButton_Click`です。</span><span class="sxs-lookup"><span data-stu-id="203f9-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="203f9-175">詳細については、次を参照してください。[する方法: 識別子 (Visual Basic) の名前を変更](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="203f9-176">次のコードを挿入、`stackButton_Click`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="203f9-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="203f9-177">Windows フォーム デザイナーで、選択、`calendarStackButton`コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="203f9-178">**プロパティ** ウィンドウの Click イベントを設定、`stackButton_Click`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="203f9-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="203f9-179">手順 10 および 11 for、`contactsStackButton`と`tasksStackButton`コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="203f9-180">アイコンの定義</span><span class="sxs-lookup"><span data-stu-id="203f9-180">Defining Icons</span></span>  
 <span data-ttu-id="203f9-181">各`StackView`ボタンに関連付けられているアイコンがあります。</span><span class="sxs-lookup"><span data-stu-id="203f9-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="203f9-182">便宜上、各アイコンとして表されます、Base64 でエンコードされた文字列の前に逆シリアル化する、<xref:System.Drawing.Bitmap>から作成します。</span><span class="sxs-lookup"><span data-stu-id="203f9-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="203f9-183">実稼働環境でのリソースとしてビットマップ データを格納して、アイコン、Windows フォーム デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="203f9-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="203f9-184">詳細については、次を参照してください。[する方法: Windows フォームの背景画像の追加](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="203f9-185">アイコンを定義する</span><span class="sxs-lookup"><span data-stu-id="203f9-185">To define icons</span></span>  
  
1.  <span data-ttu-id="203f9-186">コード エディターに次のコードを挿入する、`StackView`クラス定義です。</span><span class="sxs-lookup"><span data-stu-id="203f9-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="203f9-187">このコードでのビットマップは初期化、<xref:System.Windows.Forms.ToolStripButton>アイコン。</span><span class="sxs-lookup"><span data-stu-id="203f9-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="203f9-188">呼び出しを追加、`InitializeImages`メソッドで、`StackView`クラスのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="203f9-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="203f9-189">カスタム レンダラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="203f9-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="203f9-190">要素の大部分をカスタマイズすることができます、`StackView`から派生するクラスを実装する、コントロール、<xref:System.Windows.Forms.ToolStripRenderer>クラスです。</span><span class="sxs-lookup"><span data-stu-id="203f9-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="203f9-191">この手順では、実装、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>グリップをカスタマイズしのグラデーションの背景を描画するクラス、<xref:System.Windows.Forms.ToolStripButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="203f9-192">カスタム レンダラーを実装するには</span><span class="sxs-lookup"><span data-stu-id="203f9-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="203f9-193">次のコードを挿入、`StackView`定義を制御します。</span><span class="sxs-lookup"><span data-stu-id="203f9-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="203f9-194">定義、`StackRenderer`クラスが優先、 <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>、 <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>、および<xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground>独自の外観を生成するメソッド。</span><span class="sxs-lookup"><span data-stu-id="203f9-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="203f9-195">`StackView`コントロールのコンス トラクターの新しいインスタンスを作成、`StackRenderer`クラスし、このインスタンスに割り当てる、`stackStrip`コントロールの<xref:System.Windows.Forms.ToolStrip.Renderer%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="203f9-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="203f9-196">StackView コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="203f9-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="203f9-197">`StackView`から派生したコントロール、<xref:System.Windows.Forms.UserControl>クラスです。</span><span class="sxs-lookup"><span data-stu-id="203f9-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="203f9-198">そのため、コントロールをテストすることができます、 **UserControl Test Container**です。</span><span class="sxs-lookup"><span data-stu-id="203f9-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="203f9-199">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="203f9-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="203f9-200">StackView コントロールをテストするには</span><span class="sxs-lookup"><span data-stu-id="203f9-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="203f9-201">F5 キーを押して、プロジェクトをビルドし、開始、 **UserControl テスト コンテナー**です。</span><span class="sxs-lookup"><span data-stu-id="203f9-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="203f9-202">ボタンの上にポインターを移動、`StackView`を制御して、選択した状態の外観を表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="203f9-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="203f9-203">次の手順</span><span class="sxs-lookup"><span data-stu-id="203f9-203">Next Steps</span></span>  
 <span data-ttu-id="203f9-204">このチュートリアルでは、Office XP コントロールのプロフェッショナルな外観とカスタムのクライアントを再利用可能なコントロールを作成しました。</span><span class="sxs-lookup"><span data-stu-id="203f9-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="203f9-205">使用することができます、<xref:System.Windows.Forms.ToolStrip>ファミリの他のさまざまな目的のコントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="203f9-206">コントロールのショートカット メニューを作成する<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="203f9-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="203f9-207">詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="203f9-208">フォームを自動的に設定された標準のメニューを作成します。</span><span class="sxs-lookup"><span data-stu-id="203f9-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="203f9-209">詳細については、次を参照してください。[チュートリアル: 標準メニュー項目をフォームに](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="203f9-210">ドッキングとマルチ ドキュメント インターフェイス (MDI) フォームを作成する<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="203f9-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="203f9-211">詳細については、次を参照してください。[する方法: メニューのマージと ToolStrip コントロールを MDI フォームを作成](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="203f9-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203f9-212">参照</span><span class="sxs-lookup"><span data-stu-id="203f9-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="203f9-213">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="203f9-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="203f9-214">方法: フォームに標準メニュー項目を追加する</span><span class="sxs-lookup"><span data-stu-id="203f9-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
