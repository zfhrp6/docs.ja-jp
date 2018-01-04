---
title: "チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7731456cfcf35cd16b1df304fee4f4c138db84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="e53d0-102">チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="e53d0-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="e53d0-103">このトピックでは、Windows フォーム ベースのアプリケーションで使用する Windows Presentation Foundation (WPF) コントロールを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="e53d0-104">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e53d0-105">プロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="e53d0-105">Create the project.</span></span>  
  
-   <span data-ttu-id="e53d0-106">新しい WPF コントロールを作成する。</span><span class="sxs-lookup"><span data-stu-id="e53d0-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="e53d0-107">新しい WPF コントロールを Windows フォームに追加する。</span><span class="sxs-lookup"><span data-stu-id="e53d0-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="e53d0-108">WPF コントロールは <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e53d0-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e53d0-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e53d0-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e53d0-111">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e53d0-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e53d0-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e53d0-112">Prerequisites</span></span>  
 <span data-ttu-id="e53d0-113">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="e53d0-114">。</span><span class="sxs-lookup"><span data-stu-id="e53d0-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="e53d0-115">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="e53d0-115">Creating the Project</span></span>  
 <span data-ttu-id="e53d0-116">まず、Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e53d0-117">WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="e53d0-118">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="e53d0-118">To create the project</span></span>  
  
-   <span data-ttu-id="e53d0-119">Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`HostingWpf`です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="e53d0-120">新しい WPF コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="e53d0-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="e53d0-121">新しい WPF コントロールを作成し、プロジェクトに追加するのは、プロジェクトへの他の項目の追加と同じくらい簡単です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="e53d0-122">Windows フォーム デザイナーは特定の種類という名前のコントロールの*複合コントロール*、または*ユーザー コントロール*です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="e53d0-123">WPF ユーザー コントロールの詳細については、「<xref:System.Windows.Controls.UserControl>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e53d0-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e53d0-124">WPF の <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> の種類は、同じ <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType> という名前を持つ、Windows フォームで提供されるユーザー コントロールの種類とは区別されます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="e53d0-125">新しい WPF コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="e53d0-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="e53d0-126">**ソリューション エクスプ ローラー**、追加、新しい**WPF ユーザー コントロール ライブラリ**プロジェクトがソリューションにします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="e53d0-127">このコントロール ライブラリの既定の名前である `WpfControlLibrary1` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="e53d0-128">既定のコントロールの名前は `UserControl1.xaml` です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="e53d0-129">新しいコントロールを追加すると次の影響があります。</span><span class="sxs-lookup"><span data-stu-id="e53d0-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="e53d0-130">ファイル UserControl1.xaml が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="e53d0-131">ファイル UserControl1.xaml.cs または UserControl1.xaml.vb のいずれかが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="e53d0-132">このファイルには、イベント ハンドラーとその他の実装のための分離コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e53d0-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="e53d0-133">WPF アセンブリへの参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="e53d0-134">ファイル UserControl1.xaml が [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] で開きます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e53d0-135">デザイン ビューで `UserControl1` が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="e53d0-136">詳細については、次を参照してください。[する方法: Select およびデザイン サーフェイス上の要素の移動](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474)です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="e53d0-137">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="e53d0-138">**ツールボックス**、ドラッグ、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>コントロールをデザイン画面にします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="e53d0-139">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**ホストするコンテンツの**します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e53d0-140">一般的には、もう少し高度な WPF コンテンツをホストしてください。</span><span class="sxs-lookup"><span data-stu-id="e53d0-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="e53d0-141">ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> コントロールを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e53d0-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="e53d0-142">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="e53d0-143">WPF コントロールを Windows フォームに追加する</span><span class="sxs-lookup"><span data-stu-id="e53d0-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="e53d0-144">新しい WPF コントロールは、フォームで使用可能な状態です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="e53d0-145">Windows フォームは、<xref:System.Windows.Forms.Integration.ElementHost> コントロールを使用して、WPF コンテンツをホストします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="e53d0-146">WPF コントロールを Windows フォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="e53d0-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="e53d0-147">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="e53d0-148">**ツールボックス**、というラベルのタブを見つける**WPFUserControlLibrary WPF ユーザー コントロール**です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="e53d0-149">`UserControl1` のインスタンスをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="e53d0-150">WPF コントロールをホストするためのフォームの上に、<xref:System.Windows.Forms.Integration.ElementHost> コントロールが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="e53d0-151"><xref:System.Windows.Forms.Integration.ElementHost>コントロールの名前は`elementHost1`し、[、**プロパティ**] ウィンドウで確認できます、<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティに設定されている**UserControl1**です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="e53d0-152">WPF アセンブリへの参照がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e53d0-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="e53d0-153">`elementHost1` コントロールに、使用可能なホスティング オプションを示すスマート タグ パネルがあります。</span><span class="sxs-lookup"><span data-stu-id="e53d0-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="e53d0-154">**ElementHost タスク**スマート タグ パネルで、**親コンテナーにドッキング**です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="e53d0-155">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e53d0-156">次の手順</span><span class="sxs-lookup"><span data-stu-id="e53d0-156">Next Steps</span></span>  
 <span data-ttu-id="e53d0-157">Windows フォームと WPF は異なるテクノロジですが、密接に相互運用するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="e53d0-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="e53d0-158">アプリケーションに高度な外観と動作を提供するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="e53d0-159">WPF ページで Windows フォーム コントロールをホストします。</span><span class="sxs-lookup"><span data-stu-id="e53d0-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="e53d0-160">詳細については、次を参照してください。[チュートリアル: WPF では、Windows フォーム コントロールをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="e53d0-161">WPF コンテンツに Windows フォームの視覚スタイルを適用します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="e53d0-162">詳細については、次を参照してください。[する方法: ハイブリッド アプリケーションで Visual スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="e53d0-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="e53d0-163">WPF コンテンツのスタイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-163">Change the style of your WPF content.</span></span> <span data-ttu-id="e53d0-164">詳細については、次を参照してください。[チュートリアル: WPF コンテンツのスタイル処理の](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)します。</span><span class="sxs-lookup"><span data-stu-id="e53d0-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53d0-165">参照</span><span class="sxs-lookup"><span data-stu-id="e53d0-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="e53d0-166">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="e53d0-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="e53d0-167">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="e53d0-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="e53d0-168">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="e53d0-168">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
