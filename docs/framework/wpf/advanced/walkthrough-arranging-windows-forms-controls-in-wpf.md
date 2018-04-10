---
title: 'チュートリアル: WPF での Windows フォーム コントロールの配置'
ms.custom: ''
ms.date: 04/03/2018
ms.prod: .net-framework
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3129b4128444530b1277299f3f95ce49232421
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="8bf6d-102">チュートリアル: WPF での Windows フォーム コントロールの配置</span><span class="sxs-lookup"><span data-stu-id="8bf6d-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="8bf6d-103">このチュートリアルで使用する方法[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を整列するレイアウト機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハイブリッド アプリケーションでのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="8bf6d-104">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="8bf6d-105">プロジェクトの作成。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="8bf6d-106">既定のレイアウト設定の使用。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="8bf6d-107">コンテンツに合わせたサイズの変更。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="8bf6d-108">絶対配置の使用。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="8bf6d-109">サイズの明示的な指定。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="8bf6d-110">レイアウト プロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="8bf6d-111">z オーダーの制限の理解。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="8bf6d-112">ドッキング。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-112">Docking.</span></span>  
  
-   <span data-ttu-id="8bf6d-113">可視性の設定。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="8bf6d-114">伸縮しないコントロールのホスト。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="8bf6d-115">スケーリング。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-115">Scaling.</span></span>  
  
-   <span data-ttu-id="8bf6d-116">回転。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-116">Rotating.</span></span>  
  
-   <span data-ttu-id="8bf6d-117">パディングとマージンの設定。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="8bf6d-118">動的レイアウト コンテナーの使用。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="8bf6d-119">このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WPF サンプルでの Windows フォーム コントロールの配置](http://go.microsoft.com/fwlink/?LinkID=159971)です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="8bf6d-120">理解する必要が完了したら、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]レイアウトの機能で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8bf6d-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8bf6d-121">Prerequisites</span></span>  
 <span data-ttu-id="8bf6d-122">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="8bf6d-123">。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8bf6d-124">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="8bf6d-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="8bf6d-125">プロジェクトを作成し、設定するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="8bf6d-126">という名前の WPF アプリケーション プロジェクトを作成する`WpfLayoutHostingWf`です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="8bf6d-127">ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="8bf6d-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="8bf6d-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="8bf6d-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="8bf6d-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="8bf6d-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="8bf6d-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="8bf6d-131">MainWindow.xaml をダブルクリックして、XAML ビューで開きます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="8bf6d-132"><xref:System.Windows.Window>要素では、次の追加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間のマッピング。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="8bf6d-133"><xref:System.Windows.Controls.Grid>要素セット、<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを`true`5 つの行および 3 つの列を定義します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="8bf6d-134">既定のレイアウト設定の使用</span><span class="sxs-lookup"><span data-stu-id="8bf6d-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="8bf6d-135">既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、ホスト型のレイアウトで処理[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="8bf6d-136">既定のレイアウト設定を使用するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="8bf6d-137">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="8bf6d-138">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>コントロールに表示され、<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="8bf6d-140">ホストされるコントロールは、その内容に基づいてサイズでは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のサイズは、ホストされるコントロールに対応します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="8bf6d-141">コンテンツに合わせたサイズの変更</span><span class="sxs-lookup"><span data-stu-id="8bf6d-141">Sizing to Content</span></span>  
 <span data-ttu-id="8bf6d-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の内容を正しく表示するため、ホストされるコントロールがサイズを調整することを確認します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="8bf6d-143">コンテンツに合わせてサイズ変更するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-143">To size to content</span></span>  
  
1.  <span data-ttu-id="8bf6d-144">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="8bf6d-145">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-146">2 つの新しいボタン コントロールのフォント サイズを大きく、長いテキスト文字列が正しく表示するサイズは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストされるコントロールに合わせて要素のサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="8bf6d-147">絶対配置の使用</span><span class="sxs-lookup"><span data-stu-id="8bf6d-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="8bf6d-148">絶対配置を使用する配置、<xref:System.Windows.Forms.Integration.WindowsFormsHost>任意の場所で、ユーザー インターフェイス (UI) 要素です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="8bf6d-149">絶対配置を使用するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="8bf6d-150">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="8bf6d-151">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost>のグリッド セルの上にあるから 20 ピクセル、左端から 20 ピクセル要素が配置されます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="8bf6d-153">サイズの明示的な指定</span><span class="sxs-lookup"><span data-stu-id="8bf6d-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="8bf6d-154">サイズを指定することができます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を使用して、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="8bf6d-155">サイズを明示的に指定するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="8bf6d-156">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="8bf6d-157">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素はこれが既定のレイアウトの設定よりも小さい 70 ピクセル、高さ、幅 50 ピクセルのサイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="8bf6d-159">内容、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがそれに応じて再配置します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="8bf6d-160">レイアウト プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="8bf6d-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="8bf6d-161">常のプロパティを使用してホストされるコントロールにレイアウトに関連するプロパティを設定、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="8bf6d-162">ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="8bf6d-163">ホストされるコントロールのレイアウトに関連するプロパティを設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]も何も起こりません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="8bf6d-164">ホストされているコントロールでプロパティを設定した場合の結果を確認するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="8bf6d-165">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="8bf6d-166">ソリューション エクスプ ローラーで、MainWindow.xaml をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="8bf6d-167">vb または MainWindow.xaml.cs コード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="8bf6d-168">次のコードをコピー、`MainWindow`クラス定義です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="8bf6d-169">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="8bf6d-170">クリックして、 **Click me**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-170">Click the **Click me** button.</span></span> <span data-ttu-id="8bf6d-171">`button1_Click`イベント ハンドラーの設定、<xref:System.Windows.Forms.Control.Top%2A>と<xref:System.Windows.Forms.Control.Left%2A>ホストされるコントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="8bf6d-172">これにより、ホストされるコントロール内の位置を変更する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="8bf6d-173">ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="8bf6d-174">代わりに、ホストされるコントロールの入力は常に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="8bf6d-175">z オーダーの制限の理解</span><span class="sxs-lookup"><span data-stu-id="8bf6d-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="8bf6d-176">表示されている<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は常に、他の WPF 要素の上に描画し、それらは、z オーダーを受けません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-176">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="8bf6d-177">この z オーダーの動作を表示するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-177">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="8bf6d-178">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-178">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  <span data-ttu-id="8bf6d-179">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-179">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost>ラベル要素上で要素を描画します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-180">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  


## <a name="docking"></a><span data-ttu-id="8bf6d-181">ドッキング</span><span class="sxs-lookup"><span data-stu-id="8bf6d-181">Docking</span></span>  
 <span data-ttu-id="8bf6d-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素をサポートしている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ドッキングします。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="8bf6d-183">設定、<xref:System.Windows.Controls.DockPanel.Dock%2A>添付プロパティでホストされるコントロールをドッキングするのには、<xref:System.Windows.Controls.DockPanel>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-183">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="8bf6d-184">ホストされているコントロールをドッキングするには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-184">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="8bf6d-185">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-185">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="8bf6d-186">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-186">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>の右側に要素がドッキングされている、<xref:System.Windows.Controls.DockPanel>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-187">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="8bf6d-188">可視性の設定</span><span class="sxs-lookup"><span data-stu-id="8bf6d-188">Setting Visibility</span></span>  
 <span data-ttu-id="8bf6d-189">ことができます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]非表示を制御したり、設定して折りたたむこと、<xref:System.Windows.UIElement.Visibility%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-189">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="8bf6d-190">コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-190">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="8bf6d-191">コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-191">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="8bf6d-192">ホストされているコントロールの可視性を設定するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-192">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="8bf6d-193">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-193">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="8bf6d-194">MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-194">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="8bf6d-195">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-195">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="8bf6d-196">をクリックして、**を非表示 をクリックします。**を作成するボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を非表示します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-196">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="8bf6d-197">をクリックして、**を折りたたみます**を非表示にするにはボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をレイアウトから完全です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-197">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="8bf6d-198">ときに、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが折りたたまれている、周囲の要素がその領域を占有するように再配置します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-198">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="8bf6d-199">伸縮しないコントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="8bf6d-199">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="8bf6d-200">いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズが固定されているし、レイアウトで使用可能なスペースを埋めます伸縮しませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-200">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="8bf6d-201">たとえば、<xref:System.Windows.Forms.MonthCalendar>コントロールでは、固定された間隔で 1 か月が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-201">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="8bf6d-202">伸縮しないコントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-202">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="8bf6d-203">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-203">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="8bf6d-204">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-204">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-205"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がグリッド行の中央に配置が、空き領域の塗りつぶしに拡張されていません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-205">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="8bf6d-206">ウィンドウが十分な大きさの場合、ホストによって表示される 2 つ以上の月を参照してください可能性があります<xref:System.Windows.Forms.MonthCalendar>コントロールが、これらが、行の中央に配置します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-206">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="8bf6d-207">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト エンジンの中心が空き領域の塗りつぶしのサイズが変更できない要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-207">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="8bf6d-208">スケーリング</span><span class="sxs-lookup"><span data-stu-id="8bf6d-208">Scaling</span></span>  
 <span data-ttu-id="8bf6d-209">WPF 要素とは異なりは、ほとんどの Windows フォーム コントロールは継続的にスケーラブルなではありません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-209">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="8bf6d-210">オーバーライドするカスタム スケーリングを提供する、<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-210">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span> 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="8bf6d-211">既定の動作を使用してホストされているコントロールをスケーリングするには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-211">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="8bf6d-212">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-212">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="8bf6d-213">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-213">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-214">ホストされているコントロールとその周りの要素は、0.5 倍でスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-214">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="8bf6d-215">ただし、ホストされているコントロールのフォントはスケーリングされません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-215">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="8bf6d-216">回転</span><span class="sxs-lookup"><span data-stu-id="8bf6d-216">Rotating</span></span>  
 <span data-ttu-id="8bf6d-217">WPF 要素とは異なり、Windows フォーム コントロールが回転にサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-217">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="8bf6d-218"><xref:System.Windows.Forms.Integration.WindowsFormsHost>回転変換を適用すると、要素が他の WPF 要素を回転させません。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-218">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="8bf6d-219">180 度を発生させます以外の値を回転、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>イベント。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-219">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="8bf6d-220">ハイブリッド アプリケーションでの回転の効果を確認するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-220">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="8bf6d-221">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-221">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="8bf6d-222">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-222">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-223">ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-223">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="8bf6d-224">要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-224">You may have to resize the window to see the elements.</span></span>  
 

## <a name="setting-padding-and-margins"></a><span data-ttu-id="8bf6d-225">パディングとマージンの設定</span><span class="sxs-lookup"><span data-stu-id="8bf6d-225">Setting Padding and Margins</span></span>  
 <span data-ttu-id="8bf6d-226">パディングと余白の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトは、埋め込みと余白のような[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-226">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="8bf6d-227">設定するだけ、<xref:System.Windows.Controls.Control.Padding%2A>と<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-227">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="8bf6d-228">ホストされているコントロールのパディングとマージンを設定するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-228">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="8bf6d-229">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-229">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="8bf6d-230">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-230">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-231">パディングと余白の設定が適用されるホストに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]で、適用される同じ方法でコントロール[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-231">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="8bf6d-232">動的レイアウト コンテナーの使用</span><span class="sxs-lookup"><span data-stu-id="8bf6d-232">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="8bf6d-233"> 2 つの動的レイアウト コンテナーを提供<xref:System.Windows.Forms.FlowLayoutPanel>と<xref:System.Windows.Forms.TableLayoutPanel>です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-233"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="8bf6d-234">これらのコンテナーを使用することもできます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-234">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="8bf6d-235">動的レイアウト コンテナーを使用するには</span><span class="sxs-lookup"><span data-stu-id="8bf6d-235">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="8bf6d-236">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-236">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="8bf6d-237">MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-237">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="8bf6d-238">呼び出しを追加、`InitializeFlowLayoutPanel`コンス トラクターのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-238">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="8bf6d-239">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-239">Press F5 to build and run the application.</span></span> <span data-ttu-id="8bf6d-240"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の設定、 <xref:System.Windows.Controls.DockPanel>、および<xref:System.Windows.Forms.FlowLayoutPanel>、既定では、その子コントロールを配置<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>です。</span><span class="sxs-lookup"><span data-stu-id="8bf6d-240">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf6d-241">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bf6d-241">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="8bf6d-242">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="8bf6d-242">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="8bf6d-243">WindowsFormsHost 要素のレイアウトに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="8bf6d-243">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="8bf6d-244">WPF のサンプルでのフォーム コントロールのウィンドウの配置</span><span class="sxs-lookup"><span data-stu-id="8bf6d-244">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="8bf6d-245">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="8bf6d-245">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="8bf6d-246">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="8bf6d-246">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
