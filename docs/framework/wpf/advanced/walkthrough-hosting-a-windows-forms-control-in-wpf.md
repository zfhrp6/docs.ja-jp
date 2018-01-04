---
title: "チュートリアル: WPF での Windows フォーム コントロールのホスト"
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
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38b50c90f653238d44401bac917645cd7f293681
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="6ebef-102">チュートリアル: WPF での Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="6ebef-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="6ebef-103">豊富な機能セットには、多くのコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ebef-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="6ebef-104">ただし、場合がありますも使用する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。</span><span class="sxs-lookup"><span data-stu-id="6ebef-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="6ebef-105">たとえば、既存のかなりの投資がある[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール、またはする必要があります、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ユニークな機能を提供するコントロール。</span><span class="sxs-lookup"><span data-stu-id="6ebef-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="6ebef-106">このチュートリアルでは、ホストする方法、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>の control 権限、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードを使用してページ。</span><span class="sxs-lookup"><span data-stu-id="6ebef-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>  
  
 <span data-ttu-id="6ebef-107">このチュートリアルで説明するタスクの完全なコードについては、次を参照してください。 [WPF サンプル Windows フォーム コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=160057)です。</span><span class="sxs-lookup"><span data-stu-id="6ebef-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6ebef-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6ebef-108">Prerequisites</span></span>  
 <span data-ttu-id="6ebef-109">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="6ebef-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="6ebef-110">。</span><span class="sxs-lookup"><span data-stu-id="6ebef-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="6ebef-111">Windows フォーム コントロールをホストしています。</span><span class="sxs-lookup"><span data-stu-id="6ebef-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="6ebef-112">MaskedTextBox コントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="6ebef-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="6ebef-113">という名前の WPF アプリケーション プロジェクトを作成する`HostingWfInWpf`です。</span><span class="sxs-lookup"><span data-stu-id="6ebef-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>  
  
2.  <span data-ttu-id="6ebef-114">次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="6ebef-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="6ebef-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="6ebef-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="6ebef-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="6ebef-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="6ebef-117">MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6ebef-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="6ebef-118">名前、<xref:System.Windows.Controls.Grid>要素`grid1`です。</span><span class="sxs-lookup"><span data-stu-id="6ebef-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  <span data-ttu-id="6ebef-119">[デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。</span><span class="sxs-lookup"><span data-stu-id="6ebef-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="6ebef-120">[プロパティ] ウィンドウ、**イベント**タブです。</span><span class="sxs-lookup"><span data-stu-id="6ebef-120">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="6ebef-121">ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。</span><span class="sxs-lookup"><span data-stu-id="6ebef-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="6ebef-122">処理する次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。</span><span class="sxs-lookup"><span data-stu-id="6ebef-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. <span data-ttu-id="6ebef-123">ファイルの上部には、次のコードを追加`Imports`または`using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6ebef-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. <span data-ttu-id="6ebef-124">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="6ebef-124">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebef-125">参照</span><span class="sxs-lookup"><span data-stu-id="6ebef-125">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="6ebef-126">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="6ebef-126">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="6ebef-127">チュートリアル: WPF での XAML を使用した Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="6ebef-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [<span data-ttu-id="6ebef-128">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="6ebef-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="6ebef-129">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="6ebef-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="6ebef-130">Windows フォーム コントロールおよび同等の WPF コントロール</span><span class="sxs-lookup"><span data-stu-id="6ebef-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="6ebef-131">WPF サンプル Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="6ebef-131">Hosting a Windows Forms Control in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160057)
