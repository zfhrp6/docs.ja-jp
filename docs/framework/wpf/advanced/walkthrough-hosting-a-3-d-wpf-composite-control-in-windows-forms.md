---
title: "チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2b64cacea48bbc8855cdb9ce451a13d4ad729bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="56f0e-102">チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="56f0e-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="56f0e-103">このチュートリアルでは、作成する方法、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合を制御し、ホストすることで[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールおよびフォームを使用して、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。</span><span class="sxs-lookup"><span data-stu-id="56f0e-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="56f0e-104">このチュートリアルでは、実装、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 2 つの子コントロールを格納しています。</span><span class="sxs-lookup"><span data-stu-id="56f0e-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="56f0e-105"><xref:System.Windows.Controls.UserControl> 3 次元 (3 D) 円錐型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56f0e-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="56f0e-106">3-D オブジェクトを表示することが非常に簡単、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]よりと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="56f0e-107">そのため、これがわかりやすいホスト、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>で 3-D グラフィックスを作成するクラス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="56f0e-108">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="56f0e-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="56f0e-109">作成する、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="56f0e-110">Windows フォーム ホスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="56f0e-111">ホストしている、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="56f0e-112">このチュートリアルでタスクの完全なコードについては、次を参照してください。 [Windows フォームのサンプルの 3-D WPF 複合コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=160001)です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="56f0e-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="56f0e-113">Prerequisites</span></span>  
 <span data-ttu-id="56f0e-114">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="56f0e-115">。</span><span class="sxs-lookup"><span data-stu-id="56f0e-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="56f0e-116">ユーザー コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="56f0e-117">ユーザー コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="56f0e-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="56f0e-118">という名前の WPF ユーザー コントロール ライブラリ プロジェクトを作成する`HostingWpfUserControlInWf`です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="56f0e-119">UserControl1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="56f0e-120">生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="56f0e-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="56f0e-121">このコードを定義、 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 2 つの子コントロールを格納しています。</span><span class="sxs-lookup"><span data-stu-id="56f0e-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="56f0e-122">最初の子コントロールは、<xref:System.Windows.Controls.Label?displayProperty=nameWithType>コントロール以外の 2 つ目は、 <xref:System.Windows.Controls.Viewport3D> 3-D 円錐型を表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="56f0e-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="56f0e-123">Windows フォーム ホスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="56f0e-124">ホスト プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="56f0e-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="56f0e-125">という名前の Windows アプリケーション プロジェクトを追加`WpfUserControlHost`をソリューションにします。</span><span class="sxs-lookup"><span data-stu-id="56f0e-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="56f0e-126">詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。</span><span class="sxs-lookup"><span data-stu-id="56f0e-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="56f0e-127">ソリューション エクスプ ローラーで、WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="56f0e-128">次の参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="56f0e-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="56f0e-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="56f0e-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="56f0e-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="56f0e-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="56f0e-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="56f0e-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="56f0e-132">`HostingWpfUserControlInWf` への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="56f0e-133">ソリューション エクスプ ローラーで、設定、`WpfUserControlHost`プロジェクトをスタートアップ プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="56f0e-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="56f0e-134">Windows Presentation Foundation ユーザー コントロールをホストしています。</span><span class="sxs-lookup"><span data-stu-id="56f0e-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="56f0e-135">ユーザー コントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="56f0e-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="56f0e-136">Windows フォーム デザイナーで、Form1 を開きます。</span><span class="sxs-lookup"><span data-stu-id="56f0e-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="56f0e-137">[プロパティ] ウィンドウでをクリックして**イベント**、順にダブルクリックし、<xref:System.Windows.Forms.Form.Load>イベント ハンドラーを作成するイベントです。</span><span class="sxs-lookup"><span data-stu-id="56f0e-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="56f0e-138">コード エディターが新たに生成されたに`Form1_Load`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="56f0e-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="56f0e-139">Form1.cs のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="56f0e-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="56f0e-140">`Form1_Load`イベント ハンドラーのインスタンスを作成する`UserControl1`し、追加の接続を受け付ける、<xref:System.Windows.Forms.Integration.ElementHost>子コントロールのコントロールのコレクション。</span><span class="sxs-lookup"><span data-stu-id="56f0e-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="56f0e-141"><xref:System.Windows.Forms.Integration.ElementHost>コントロールが子コントロールのフォームのコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="56f0e-142">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="56f0e-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f0e-143">参照</span><span class="sxs-lookup"><span data-stu-id="56f0e-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="56f0e-144">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="56f0e-144">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="56f0e-145">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="56f0e-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="56f0e-146">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="56f0e-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="56f0e-147">Windows フォームのサンプルでの WPF 複合コントロールをホストしています。</span><span class="sxs-lookup"><span data-stu-id="56f0e-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
