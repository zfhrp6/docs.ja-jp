---
title: "Windows フォーム コントロールおよび同等の WPF コントロール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04807b849af07a6882689e98ca9ca57d4b6840ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="d3cc6-102">Windows フォーム コントロールおよび同等の WPF コントロール</span><span class="sxs-lookup"><span data-stu-id="d3cc6-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="d3cc6-103">多く[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがある該当するショートカットは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールですが、一部[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール対応ソリューションを持つありません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="d3cc6-104">このトピックでは、2 つのテクノロジによって提供されるコントロールの種類を比較します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="d3cc6-105">常にホストへの相互運用を使用することができます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]対応でないコントロール、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="d3cc6-106">次の表では[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールおよびコンポーネントがある該当するショートカットは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]機能を制御します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="d3cc6-107">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="d3cc6-107">Windows Forms control</span></span>|<span data-ttu-id="d3cc6-108">同等の WPF コントロール</span><span class="sxs-lookup"><span data-stu-id="d3cc6-108">WPF equivalent control</span></span>|<span data-ttu-id="d3cc6-109">コメント</span><span class="sxs-lookup"><span data-stu-id="d3cc6-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="d3cc6-110">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="d3cc6-111"><xref:System.Windows.Controls.ListBox>構成します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="d3cc6-112">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="d3cc6-113"><xref:System.Windows.Controls.ComboBox>オートコンプリートによってサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="d3cc6-114"><xref:System.Windows.Controls.TextBox>2 つと<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="d3cc6-115">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="d3cc6-116"><xref:System.Windows.Controls.WrapPanel> または <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="d3cc6-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="d3cc6-117">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="d3cc6-118">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="d3cc6-119"><xref:System.Windows.Window>子ウィンドウをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="d3cc6-120">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-120">No equivalent control.</span></span>|<span data-ttu-id="d3cc6-121">F1 ヘルプはありません。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-121">No F1 Help.</span></span> <span data-ttu-id="d3cc6-122">「これは何です」ヘルプがツールヒントに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="d3cc6-123">コンテナー コントロールには、スクロールが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="d3cc6-124">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="d3cc6-125">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-125">No equivalent control.</span></span>|<span data-ttu-id="d3cc6-126">使用することができます、<xref:System.Windows.Documents.Hyperlink>フロー コンテンツ内のハイパーリンクをホストするクラス。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="d3cc6-127"><xref:System.Windows.Controls.ListView>コントロールには、読み取り専用の詳細ビューが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="d3cc6-128">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="d3cc6-129"><xref:System.Windows.Controls.Menu>コントロールのスタイル設定にはの動作と外観を概算できる、<xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="d3cc6-130">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="d3cc6-131"><xref:System.Windows.Controls.TextBox>2 つと<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="d3cc6-132"><xref:Microsoft.Win32.OpenFileDialog>クラスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ラッパー、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="d3cc6-133">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="d3cc6-134">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="d3cc6-135">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="d3cc6-136">等価コントロールなし。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="d3cc6-137"><xref:Microsoft.Win32.SaveFileDialog>クラスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ラッパー、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="d3cc6-138"><xref:System.Windows.Controls.ToolBar>構成します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="d3cc6-139"><xref:System.Windows.Controls.ToolBar>構成します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="d3cc6-140"><xref:System.Windows.Controls.ToolBar>構成します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="d3cc6-141"><xref:System.Windows.Controls.ToolBar>構成します。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="d3cc6-142">コンテナー コントロールには、スクロールが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="d3cc6-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d3cc6-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="d3cc6-144"><xref:System.Windows.Controls.Frame>コントロールが HTML ページをホストできます。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="d3cc6-145">以降では、 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]、<xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>コントロールは、HTML ページともバックアップをホストできる、<xref:System.Windows.Controls.Frame>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-145">Starting in the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3cc6-146">参照</span><span class="sxs-lookup"><span data-stu-id="d3cc6-146">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d3cc6-147">Windows の WPF デザイナーの開発者をフォームします。</span><span class="sxs-lookup"><span data-stu-id="d3cc6-147">WPF Designer for Windows Forms Developers</span></span>](http://msdn.microsoft.com/en-us/47ad0909-e89b-4996-b4ac-874d929f94ca)  
 [<span data-ttu-id="d3cc6-148">チュートリアル: WPF での Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="d3cc6-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="d3cc6-149">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="d3cc6-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="d3cc6-150">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="d3cc6-150">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
