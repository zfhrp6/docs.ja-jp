---
title: "チュートリアル: WPF での Windows フォーム コントロールの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480d61f6ca2aa67e0de48030655a6368c70554f4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="2c6ad-102">チュートリアル: WPF での Windows フォーム コントロールの配置</span><span class="sxs-lookup"><span data-stu-id="2c6ad-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="2c6ad-103">このチュートリアルで使用する方法[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を整列するレイアウト機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハイブリッド アプリケーションでのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="2c6ad-104">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="2c6ad-105">プロジェクトの作成。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="2c6ad-106">既定のレイアウト設定の使用。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="2c6ad-107">コンテンツに合わせたサイズの変更。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="2c6ad-108">絶対配置の使用。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="2c6ad-109">サイズの明示的な指定。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="2c6ad-110">レイアウト プロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="2c6ad-111">z オーダーの制限の理解。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="2c6ad-112">ドッキング。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-112">Docking.</span></span>  
  
-   <span data-ttu-id="2c6ad-113">可視性の設定。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="2c6ad-114">伸縮しないコントロールのホスト。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="2c6ad-115">スケーリング。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-115">Scaling.</span></span>  
  
-   <span data-ttu-id="2c6ad-116">回転。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-116">Rotating.</span></span>  
  
-   <span data-ttu-id="2c6ad-117">パディングとマージンの設定。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="2c6ad-118">動的レイアウト コンテナーの使用。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="2c6ad-119">このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WPF サンプルでの Windows フォーム コントロールの配置](http://go.microsoft.com/fwlink/?LinkID=159971)です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="2c6ad-120">理解する必要が完了したら、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]レイアウトの機能で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2c6ad-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2c6ad-121">Prerequisites</span></span>  
 <span data-ttu-id="2c6ad-122">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="2c6ad-123">。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2c6ad-124">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2c6ad-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="2c6ad-125">プロジェクトを作成し、設定するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="2c6ad-126">という名前の WPF アプリケーション プロジェクトを作成する`WpfLayoutHostingWf`です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="2c6ad-127">ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="2c6ad-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="2c6ad-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="2c6ad-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="2c6ad-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="2c6ad-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="2c6ad-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="2c6ad-131">MainWindow.xaml をダブルクリックして、XAML ビューで開きます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="2c6ad-132"><xref:System.Windows.Window>要素では、次の追加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間のマッピング。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="2c6ad-133"><xref:System.Windows.Controls.Grid>要素セット、<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを`true`5 つの行および 3 つの列を定義します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="2c6ad-134">既定のレイアウト設定の使用</span><span class="sxs-lookup"><span data-stu-id="2c6ad-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="2c6ad-135">既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、ホスト型のレイアウトで処理[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="2c6ad-136">既定のレイアウト設定を使用するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="2c6ad-137">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="2c6ad-138">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>コントロールに表示され、<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2c6ad-140">ホストされるコントロールは、その内容に基づいてサイズでは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のサイズは、ホストされるコントロールに対応します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="2c6ad-141">コンテンツに合わせたサイズの変更</span><span class="sxs-lookup"><span data-stu-id="2c6ad-141">Sizing to Content</span></span>  
 <span data-ttu-id="2c6ad-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の内容を正しく表示するため、ホストされるコントロールがサイズを調整することを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="2c6ad-143">コンテンツに合わせてサイズ変更するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-143">To size to content</span></span>  
  
1.  <span data-ttu-id="2c6ad-144">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="2c6ad-145">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-146">2 つの新しいボタン コントロールのフォント サイズを大きく、長いテキスト文字列が正しく表示するサイズは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストされるコントロールに合わせて要素のサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="2c6ad-147">絶対配置の使用</span><span class="sxs-lookup"><span data-stu-id="2c6ad-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="2c6ad-148">絶対配置を使用する配置、<xref:System.Windows.Forms.Integration.WindowsFormsHost>任意の場所で、ユーザー インターフェイス (UI) 要素です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="2c6ad-149">絶対配置を使用するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="2c6ad-150">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="2c6ad-151">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost>のグリッド セルの上にあるから 20 ピクセル、左端から 20 ピクセル要素が配置されます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="2c6ad-153">サイズの明示的な指定</span><span class="sxs-lookup"><span data-stu-id="2c6ad-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="2c6ad-154">サイズを指定することができます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を使用して、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="2c6ad-155">サイズを明示的に指定するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="2c6ad-156">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="2c6ad-157">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素はこれが既定のレイアウトの設定よりも小さい 70 ピクセル、高さ、幅 50 ピクセルのサイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="2c6ad-159">内容、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがそれに応じて再配置します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="2c6ad-160">レイアウト プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="2c6ad-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="2c6ad-161">常のプロパティを使用してホストされるコントロールにレイアウトに関連するプロパティを設定、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="2c6ad-162">ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="2c6ad-163">ホストされるコントロールのレイアウトに関連するプロパティを設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]も何も起こりません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="2c6ad-164">ホストされているコントロールでプロパティを設定した場合の結果を確認するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="2c6ad-165">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="2c6ad-166">ソリューション エクスプ ローラーで、MainWindow.xaml をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="2c6ad-167">vb または MainWindow.xaml.cs コード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="2c6ad-168">次のコードをコピー、`MainWindow`クラス定義です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="2c6ad-169">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="2c6ad-170">クリックして、 **Click me**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-170">Click the **Click me** button.</span></span> <span data-ttu-id="2c6ad-171">`button1_Click`イベント ハンドラーの設定、<xref:System.Windows.Forms.Control.Top%2A>と<xref:System.Windows.Forms.Control.Left%2A>ホストされるコントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="2c6ad-172">これにより、ホストされるコントロール内の位置を変更する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="2c6ad-173">ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="2c6ad-174">代わりに、ホストされるコントロールの入力は常に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="2c6ad-175">z オーダーの制限の理解</span><span class="sxs-lookup"><span data-stu-id="2c6ad-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="2c6ad-176">既定では、表示されている<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は常に他の上に描画[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素、および、z オーダーで影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-176">By default, visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="2c6ad-177">Z オーダーを有効にするには設定、<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を true に、<xref:System.Windows.Interop.HwndHost.CompositionMode%2A>プロパティを<xref:System.Windows.Interop.CompositionMode.Full>または<xref:System.Windows.Interop.CompositionMode.OutputOnly>です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-177">To enable z-ordering, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-default-z-order-behavior"></a><span data-ttu-id="2c6ad-178">既定の z オーダーの動作を確認するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-178">To see the default z-order behavior</span></span>  
  
1.  <span data-ttu-id="2c6ad-179">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-179">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  <span data-ttu-id="2c6ad-180">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-180">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>ラベル要素上で要素を描画します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-181">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a><span data-ttu-id="2c6ad-182">IsRedirected が true の場合に z オーダーの動作を確認するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-182">To see the z-order behavior when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="2c6ad-183">前の z オーダーの例を次の XAML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-183">Replace the previous z-order example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     <span data-ttu-id="2c6ad-184">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-184">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-185">経由で、label 要素が描画された、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-185">The label element is painted over the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="docking"></a><span data-ttu-id="2c6ad-186">ドッキング</span><span class="sxs-lookup"><span data-stu-id="2c6ad-186">Docking</span></span>  
 <span data-ttu-id="2c6ad-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をサポートしている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ドッキングします。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="2c6ad-188">設定、<xref:System.Windows.Controls.DockPanel.Dock%2A>添付プロパティでホストされるコントロールをドッキングするのには、<xref:System.Windows.Controls.DockPanel>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-188">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="2c6ad-189">ホストされているコントロールをドッキングするには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-189">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="2c6ad-190">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-190">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="2c6ad-191">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-191">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-192"><xref:System.Windows.Forms.Integration.WindowsFormsHost>の右側に要素がドッキングされている、<xref:System.Windows.Controls.DockPanel>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-192">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="2c6ad-193">可視性の設定</span><span class="sxs-lookup"><span data-stu-id="2c6ad-193">Setting Visibility</span></span>  
 <span data-ttu-id="2c6ad-194">ことができます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]非表示を制御したり、設定して折りたたむこと、<xref:System.Windows.UIElement.Visibility%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-194">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="2c6ad-195">コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-195">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="2c6ad-196">コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-196">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="2c6ad-197">ホストされているコントロールの可視性を設定するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-197">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="2c6ad-198">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-198">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="2c6ad-199">MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-199">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="2c6ad-200">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-200">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="2c6ad-201">をクリックして、**を非表示 をクリックします。**を作成するボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を非表示します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-201">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="2c6ad-202">をクリックして、**を折りたたみます**を非表示にするにはボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をレイアウトから完全です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-202">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="2c6ad-203">ときに、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが折りたたまれている、周囲の要素がその領域を占有するように再配置します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-203">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="2c6ad-204">伸縮しないコントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="2c6ad-204">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="2c6ad-205">いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズが固定されているし、レイアウトで使用可能なスペースを埋めます伸縮しませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-205">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="2c6ad-206">たとえば、<xref:System.Windows.Forms.MonthCalendar>コントロールでは、固定された間隔で 1 か月が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-206">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="2c6ad-207">伸縮しないコントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-207">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="2c6ad-208">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-208">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="2c6ad-209">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-209">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-210"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がグリッド行の中央に配置が、空き領域の塗りつぶしに拡張されていません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-210">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="2c6ad-211">ウィンドウが十分な大きさの場合、ホストによって表示される 2 つ以上の月を参照してください可能性があります<xref:System.Windows.Forms.MonthCalendar>コントロールが、これらが、行の中央に配置します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-211">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="2c6ad-212">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト エンジンの中心が空き領域の塗りつぶしのサイズが変更できない要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-212">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="2c6ad-213">スケーリング</span><span class="sxs-lookup"><span data-stu-id="2c6ad-213">Scaling</span></span>  
 <span data-ttu-id="2c6ad-214">異なり[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素、ほとんど[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールにスケーラブルな継続的にはできません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-214">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, most [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls are not continuously scalable.</span></span> <span data-ttu-id="2c6ad-215">既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素可能な場合は、ホストされるコントロールのスケールを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-215">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element scales its hosted control when possible.</span></span>  <span data-ttu-id="2c6ad-216">本格的なスケーリングを有効にするには設定、<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を true に、<xref:System.Windows.Interop.HwndHost.CompositionMode%2A>プロパティを<xref:System.Windows.Interop.CompositionMode.Full>または<xref:System.Windows.Interop.CompositionMode.OutputOnly>です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-216">To enable full-fledged scaling, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="2c6ad-217">既定の動作を使用してホストされているコントロールをスケーリングするには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-217">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="2c6ad-218">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-218">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="2c6ad-219">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-219">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-220">ホストされているコントロールとその周りの要素は、0.5 倍でスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-220">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="2c6ad-221">ただし、ホストされているコントロールのフォントはスケーリングされません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-221">However, the hosted control's font is not scaled.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a><span data-ttu-id="2c6ad-222">IsRedirected を true に設定してホストされているコントロールをスケーリングするには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-222">To scale a hosted control by setting IsRedirected to true</span></span>  
  
1.  <span data-ttu-id="2c6ad-223">前述のスケーリングの例を、次の XAML に書き換えます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-223">Replace the previous scaling example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  <span data-ttu-id="2c6ad-224">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-224">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-225">ホストされているコントロール、その周りの要素、ホストされているコントロールのフォントは 0.5 倍でスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-225">The hosted control, its surrounding elements, and the hosted control's font are scaled by a factor of 0.5.</span></span>  
  
## <a name="rotating"></a><span data-ttu-id="2c6ad-226">回転</span><span class="sxs-lookup"><span data-stu-id="2c6ad-226">Rotating</span></span>  
 <span data-ttu-id="2c6ad-227">異なり[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールでは回転をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-227">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls do not support rotation.</span></span> <span data-ttu-id="2c6ad-228">既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が他の回転させません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]回転変換を適用するときの要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-228">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements when a rotation transformation is applied.</span></span> <span data-ttu-id="2c6ad-229">180 度を発生させます以外の値を回転、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>イベント。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-229">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>  <span data-ttu-id="2c6ad-230">任意の角度に回転を有効にするには設定、<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を true に、<xref:System.Windows.Interop.HwndHost.CompositionMode%2A>プロパティを<xref:System.Windows.Interop.CompositionMode.Full>または<xref:System.Windows.Interop.CompositionMode.OutputOnly>です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-230">To enable rotating to any angle, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="2c6ad-231">ハイブリッド アプリケーションでの回転の効果を確認するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-231">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="2c6ad-232">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-232">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="2c6ad-233">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-233">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-234">ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-234">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="2c6ad-235">要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-235">You may have to resize the window to see the elements.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a><span data-ttu-id="2c6ad-236">IsRedirected が true の場合に、ハイブリッド アプリケーションで回転の効果を確認するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-236">To see the effect of rotation in a hybrid application when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="2c6ad-237">前述の回転の例を、次の XAML に書き換えます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-237">Replace the previous rotation example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  <span data-ttu-id="2c6ad-238">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-239">ホストされているコントロールが回転します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-239">The hosted control is rotated.</span></span>  <span data-ttu-id="2c6ad-240">なお、<xref:System.Windows.Media.RotateTransform.Angle%2A>プロパティは、任意の値に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-240">Note that the <xref:System.Windows.Media.RotateTransform.Angle%2A> property can be set to any value.</span></span> <span data-ttu-id="2c6ad-241">要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-241">You may have to resize the window to see the elements.</span></span>  
  
## <a name="setting-padding-and-margins"></a><span data-ttu-id="2c6ad-242">パディングとマージンの設定</span><span class="sxs-lookup"><span data-stu-id="2c6ad-242">Setting Padding and Margins</span></span>  
 <span data-ttu-id="2c6ad-243">パディングと余白の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトは、埋め込みと余白のような[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-243">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="2c6ad-244">設定するだけ、<xref:System.Windows.Controls.Control.Padding%2A>と<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-244">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="2c6ad-245">ホストされているコントロールのパディングとマージンを設定するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-245">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="2c6ad-246">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-246">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="2c6ad-247">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-247">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-248">パディングと余白の設定が適用されるホストに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]で、適用される同じ方法でコントロール[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-248">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="2c6ad-249">動的レイアウト コンテナーの使用</span><span class="sxs-lookup"><span data-stu-id="2c6ad-249">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="2c6ad-250">2 つの動的レイアウト コンテナーを提供<xref:System.Windows.Forms.FlowLayoutPanel>と<xref:System.Windows.Forms.TableLayoutPanel>です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-250"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="2c6ad-251">これらのコンテナーを使用することもできます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトです。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-251">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="2c6ad-252">動的レイアウト コンテナーを使用するには</span><span class="sxs-lookup"><span data-stu-id="2c6ad-252">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="2c6ad-253">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-253">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="2c6ad-254">MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-254">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="2c6ad-255">呼び出しを追加、`InitializeFlowLayoutPanel`コンス トラクターのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-255">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="2c6ad-256">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-256">Press F5 to build and run the application.</span></span> <span data-ttu-id="2c6ad-257"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の設定、 <xref:System.Windows.Controls.DockPanel>、および<xref:System.Windows.Forms.FlowLayoutPanel>、既定では、その子コントロールを配置<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>です。</span><span class="sxs-lookup"><span data-stu-id="2c6ad-257">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6ad-258">参照</span><span class="sxs-lookup"><span data-stu-id="2c6ad-258">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="2c6ad-259">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="2c6ad-259">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="2c6ad-260">WindowsFormsHost 要素のレイアウトに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="2c6ad-260">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="2c6ad-261">WPF のサンプルでのフォーム コントロールのウィンドウの配置</span><span class="sxs-lookup"><span data-stu-id="2c6ad-261">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="2c6ad-262">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="2c6ad-262">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="2c6ad-263">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="2c6ad-263">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
