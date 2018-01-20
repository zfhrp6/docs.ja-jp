---
title: "チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afde62d07c009de4612aa44ebbd81b5a71ef36e5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="610fb-102">チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置</span><span class="sxs-lookup"><span data-stu-id="610fb-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="610fb-103">このチュートリアルでは、固定やスナップ線などの Windows フォームのレイアウト機能を使用して、Windows Presentation Foundation (WPF) コントロールを配置する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="610fb-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>  
  
 <span data-ttu-id="610fb-104">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="610fb-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="610fb-105">プロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="610fb-105">Create the project.</span></span>  
  
-   <span data-ttu-id="610fb-106">WPF コントロールを作成する。</span><span class="sxs-lookup"><span data-stu-id="610fb-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="610fb-107">レイアウト パネルで WPF コントロールをホストする。</span><span class="sxs-lookup"><span data-stu-id="610fb-107">Host WPF controls in a layout panel.</span></span>  
  
-   <span data-ttu-id="610fb-108">WPF コントロールを配置するスナップ線を使用する。</span><span class="sxs-lookup"><span data-stu-id="610fb-108">Use snaplines to align WPF controls.</span></span>  
  
-   <span data-ttu-id="610fb-109">WPF コントロールを固定してドッキングする。</span><span class="sxs-lookup"><span data-stu-id="610fb-109">Anchor and dock WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="610fb-110">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="610fb-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="610fb-111">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="610fb-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="610fb-112">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="610fb-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="610fb-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="610fb-113">Prerequisites</span></span>  
 <span data-ttu-id="610fb-114">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="610fb-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="610fb-115">。</span><span class="sxs-lookup"><span data-stu-id="610fb-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="610fb-116">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="610fb-116">Creating the Project</span></span>  
 <span data-ttu-id="610fb-117">まず、Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="610fb-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="610fb-118">WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="610fb-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="610fb-119">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="610fb-119">To create the project</span></span>  
  
-   <span data-ttu-id="610fb-120">Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`ArrangeElementHost`です。</span><span class="sxs-lookup"><span data-stu-id="610fb-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="610fb-121">WPF コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="610fb-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="610fb-122">プロジェクトに WPF コントロール型を追加したら、フォーム状に配置できます。</span><span class="sxs-lookup"><span data-stu-id="610fb-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="610fb-123">WPF コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="610fb-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="610fb-124">新しい WPF <xref:System.Windows.Controls.UserControl> をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="610fb-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="610fb-125">コントロール型の既定の名前である `UserControl1.xaml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="610fb-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="610fb-126">詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="610fb-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="610fb-127">デザイン ビューで `UserControl1` が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="610fb-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="610fb-128">詳細については、次を参照してください。[する方法: Select およびデザイン サーフェイス上の要素の移動](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474)です。</span><span class="sxs-lookup"><span data-stu-id="610fb-128">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="610fb-129">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。</span><span class="sxs-lookup"><span data-stu-id="610fb-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="610fb-130"><xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `Blue` に設定します。</span><span class="sxs-lookup"><span data-stu-id="610fb-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="610fb-131">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="610fb-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="610fb-132">レイアウト パネルで WPF コントロールをホストする</span><span class="sxs-lookup"><span data-stu-id="610fb-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="610fb-133">その他の Windows フォーム コントロールを使用するのと同じ方法で、レイアウト パネルで WPF コントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="610fb-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="610fb-134">レイアウト パネルで WPF コントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="610fb-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="610fb-135">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="610fb-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="610fb-136">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="610fb-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="610fb-137"><xref:System.Windows.Forms.TableLayoutPanel>コントロールのスマート タグ パネルで、**最後の行を削除する**です。</span><span class="sxs-lookup"><span data-stu-id="610fb-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="610fb-138">幅と高さが大きくなるよう <xref:System.Windows.Forms.TableLayoutPanel> コントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="610fb-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="610fb-139">**ツールボックス**をダブルクリックして`UserControl1`のインスタンスを作成する`UserControl1`の最初のセルで、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="610fb-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="610fb-140">`UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="610fb-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="610fb-141">**ツールボックス**をダブルクリックして`UserControl1`の 2 番目のセルで別のインスタンスを作成する、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="610fb-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="610fb-142">**ドキュメント アウトライン**ウィンドウで、`tableLayoutPanel1`です。</span><span class="sxs-lookup"><span data-stu-id="610fb-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="610fb-143">詳細については、次を参照してください。[ドキュメント アウトライン ウィンドウ](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8)します。</span><span class="sxs-lookup"><span data-stu-id="610fb-143">For more information, see [Document Outline Window](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="610fb-144">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Control.Padding%2A>プロパティを`10, 10, 10, 10`です。</span><span class="sxs-lookup"><span data-stu-id="610fb-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="610fb-145">両方の <xref:System.Windows.Forms.Integration.ElementHost> コントロールが、新しいレイアウトに収まるようにサイズ変更されました。</span><span class="sxs-lookup"><span data-stu-id="610fb-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="610fb-146">WPF コントロールを配置するスナップ線を使用する</span><span class="sxs-lookup"><span data-stu-id="610fb-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="610fb-147">スナップ線により、フォームのコントロールの配置を簡単に調整できます。</span><span class="sxs-lookup"><span data-stu-id="610fb-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="610fb-148">スナップ線を使用して、WPF コントロールも配置することができます。</span><span class="sxs-lookup"><span data-stu-id="610fb-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="610fb-149">詳細については、次を参照してください。[チュートリアル: Windows フォームを使用するスナップ線上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)です。</span><span class="sxs-lookup"><span data-stu-id="610fb-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="610fb-150">WPF コントロールを配置するスナップ線を使用するには</span><span class="sxs-lookup"><span data-stu-id="610fb-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="610fb-151">**ツールボックス**のインスタンスをドラッグ`UserControl1`フォーム上に下の領域に配置し、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="610fb-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="610fb-152">`UserControl1` のインスタンスは、`elementHost3` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="610fb-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="610fb-153">スナップ線を使用して、`elementHost3` の左端を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの左端に揃えます。</span><span class="sxs-lookup"><span data-stu-id="610fb-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="610fb-154">スナップ線を使用して、`elementHost3` のサイズを <xref:System.Windows.Forms.TableLayoutPanel> コントロールと同じ幅にします。</span><span class="sxs-lookup"><span data-stu-id="610fb-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="610fb-155">コントロール間に中央揃えのスナップ線が表示されるまで`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの方へ移動します。</span><span class="sxs-lookup"><span data-stu-id="610fb-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="610fb-156">**プロパティ**ウィンドウで、余白プロパティの値を設定する`20, 20, 20, 20`です。</span><span class="sxs-lookup"><span data-stu-id="610fb-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="610fb-157">中央揃えのスナップ線がもう一度表示されるまで、`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールから移動します。</span><span class="sxs-lookup"><span data-stu-id="610fb-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="610fb-158">中央揃えのスナップ線が、余白 20 を示すようになりました。</span><span class="sxs-lookup"><span data-stu-id="610fb-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="610fb-159">左端が `elementHost1` の左端に配置されるまで、`elementHost3` を右に移動します。</span><span class="sxs-lookup"><span data-stu-id="610fb-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="610fb-160">右端が `elementHost2` の右端に配置されるまで、`elementHost3` の幅を変更します。</span><span class="sxs-lookup"><span data-stu-id="610fb-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="610fb-161">WPF コントロールの固定およびドッキング</span><span class="sxs-lookup"><span data-stu-id="610fb-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="610fb-162">フォームでホストされている WPF コントロールは、他の Windows フォーム コントロールと同じ固定とドッキングの動作を持ちます。</span><span class="sxs-lookup"><span data-stu-id="610fb-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="610fb-163">WPF コントロールを固定してドッキングするには</span><span class="sxs-lookup"><span data-stu-id="610fb-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="610fb-164">`elementHost1` を選択します。</span><span class="sxs-lookup"><span data-stu-id="610fb-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="610fb-165">**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを**Top、Bottom、Left、Right**です。</span><span class="sxs-lookup"><span data-stu-id="610fb-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="610fb-166"><xref:System.Windows.Forms.TableLayoutPanel> コントロールを大きなサイズに変更します。</span><span class="sxs-lookup"><span data-stu-id="610fb-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="610fb-167">`elementHost1` コントロールがセルを満たすようサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="610fb-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="610fb-168">`elementHost2` を選択します。</span><span class="sxs-lookup"><span data-stu-id="610fb-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="610fb-169">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。</span><span class="sxs-lookup"><span data-stu-id="610fb-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="610fb-170">`elementHost2` コントロールがセルを満たすようサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="610fb-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="610fb-171"><xref:System.Windows.Forms.TableLayoutPanel> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="610fb-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="610fb-172"><xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Top> に設定します。</span><span class="sxs-lookup"><span data-stu-id="610fb-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="610fb-173">`elementHost3` を選択します。</span><span class="sxs-lookup"><span data-stu-id="610fb-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="610fb-174"><xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill> に設定します。</span><span class="sxs-lookup"><span data-stu-id="610fb-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="610fb-175">`elementHost3` コントロールが、フォームの残りの領域を満たすようサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="610fb-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="610fb-176">フォームのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="610fb-176">Resize the form.</span></span>  
  
     <span data-ttu-id="610fb-177">3 つすべての <xref:System.Windows.Forms.Integration.ElementHost> コントロールのサイズを適切に変更します。</span><span class="sxs-lookup"><span data-stu-id="610fb-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="610fb-178">詳細については、次を参照してください。[する方法: アンカーと TableLayoutPanel コントロールで子コントロールのドッキング](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="610fb-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610fb-179">参照</span><span class="sxs-lookup"><span data-stu-id="610fb-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="610fb-180">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="610fb-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="610fb-181">方法: デザイン時にフォームの端に合わせてコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="610fb-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="610fb-182">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="610fb-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="610fb-183">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="610fb-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="610fb-184">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="610fb-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="610fb-185">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="610fb-185">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
