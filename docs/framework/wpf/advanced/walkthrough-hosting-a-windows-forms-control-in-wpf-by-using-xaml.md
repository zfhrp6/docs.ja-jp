---
title: 'チュートリアル: WPF での、XAML を使用した Windows フォーム コントロールのホスト'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: b55a51a7ca16416b6963c57395da2f2a88a55648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548585"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="44a12-102">チュートリアル: WPF での、XAML を使用した Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="44a12-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="44a12-103"> 豊富な機能セットには、多くのコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="44a12-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="44a12-104">ただし、場合がありますも使用する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。</span><span class="sxs-lookup"><span data-stu-id="44a12-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="44a12-105">たとえば、既存のかなりの投資がある[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール、またはする必要があります、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ユニークな機能を提供するコントロール。</span><span class="sxs-lookup"><span data-stu-id="44a12-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="44a12-106">このチュートリアルでは、Windows フォームをホストする方法<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>の control 権限、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用してページ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44a12-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="44a12-107">このチュートリアルで説明するタスクの完全なコードについては、次を参照してください。[を使用して XAML サンプルでの WPF での Windows フォーム コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=160000)です。</span><span class="sxs-lookup"><span data-stu-id="44a12-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](http://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="44a12-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="44a12-108">Prerequisites</span></span>  
 <span data-ttu-id="44a12-109">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="44a12-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="44a12-110">。</span><span class="sxs-lookup"><span data-stu-id="44a12-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="44a12-111">Windows フォーム コントロールをホストしています。</span><span class="sxs-lookup"><span data-stu-id="44a12-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="44a12-112">MaskedTextBox コントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="44a12-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="44a12-113">という名前の WPF アプリケーション プロジェクトを作成する`HostingWfInWpfWithXaml`です。</span><span class="sxs-lookup"><span data-stu-id="44a12-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="44a12-114">次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="44a12-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="44a12-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="44a12-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="44a12-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="44a12-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="44a12-117">MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44a12-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="44a12-118"><xref:System.Windows.Window>要素では、次の名前空間のマッピングを追加します。</span><span class="sxs-lookup"><span data-stu-id="44a12-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="44a12-119">`wf`名前空間のマッピングは、Windows フォーム コントロールを含むアセンブリへの参照を確立します。</span><span class="sxs-lookup"><span data-stu-id="44a12-119">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="44a12-120"><xref:System.Windows.Controls.Grid>要素は、次の XAML を追加します。</span><span class="sxs-lookup"><span data-stu-id="44a12-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="44a12-121"><xref:System.Windows.Forms.MaskedTextBox>コントロールの子として作成された、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。</span><span class="sxs-lookup"><span data-stu-id="44a12-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="44a12-122">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="44a12-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a12-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="44a12-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="44a12-124">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="44a12-124">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="44a12-125">チュートリアル: WPF での Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="44a12-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="44a12-126">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="44a12-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="44a12-127">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="44a12-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="44a12-128">Windows フォーム コントロールおよび同等の WPF コントロール</span><span class="sxs-lookup"><span data-stu-id="44a12-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="44a12-129">XAML のサンプルを使用して、WPF では、Windows フォーム コントロールをホストしています。</span><span class="sxs-lookup"><span data-stu-id="44a12-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160000)
