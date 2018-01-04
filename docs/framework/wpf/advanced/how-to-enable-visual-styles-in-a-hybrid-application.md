---
title: "方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする"
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
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73f611eab7f75d1578652a8a9f5bb05d9720e851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="f4eb0-102">方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする</span><span class="sxs-lookup"><span data-stu-id="f4eb0-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="f4eb0-103">このトピックは、有効にする方法を示しています。[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]上の visual スタイル、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でホストされるコントロール、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="f4eb0-104">アプリケーションが呼び出す場合、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド、ほとんどの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが自動的に使用の visual スタイルでアプリケーションを実行時に[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="f4eb0-105">詳細については、次を参照してください。 [Visual スタイルを使用しているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-105">For more information, see [Rendering Controls with Visual Styles](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="f4eb0-106">このトピックで示すタスクの完全なコードについては、次を参照してください。[ハイブリッド アプリケーションのサンプルの Visual スタイルを有効にすると](http://go.microsoft.com/fwlink/?LinkID=159986)です。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="f4eb0-107">Windows フォーム視覚スタイルの有効化</span><span class="sxs-lookup"><span data-stu-id="f4eb0-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="f4eb0-108">Windows フォーム視覚スタイルを有効にするには</span><span class="sxs-lookup"><span data-stu-id="f4eb0-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="f4eb0-109">作成、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]という名前のアプリケーション プロジェクト`HostingWfWithVisualStyles`です。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="f4eb0-110">ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="f4eb0-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f4eb0-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="f4eb0-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f4eb0-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="f4eb0-113">ツールボックスでダブルクリックして、<xref:System.Windows.Controls.Grid>を配置するにはアイコン、<xref:System.Windows.Controls.Grid>デザイン サーフェイス上の要素。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="f4eb0-114">[プロパティ] ウィンドウでの値を設定、<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>プロパティ**自動**です。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="f4eb0-115">[デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>です。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="f4eb0-116">[プロパティ] ウィンドウ、**イベント**タブです。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="f4eb0-117">ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="f4eb0-118">MainWindow.xaml.vb または MainWindow.xaml.cs で処理する次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="f4eb0-119">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="f4eb0-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが visual スタイルで描画します。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="f4eb0-121">Windows フォーム視覚スタイルの無効化</span><span class="sxs-lookup"><span data-stu-id="f4eb0-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="f4eb0-122">Visual スタイルを無効にするには、削除するだけを呼び出し、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="f4eb0-123">Windows フォーム視覚スタイルを無効にするには</span><span class="sxs-lookup"><span data-stu-id="f4eb0-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="f4eb0-124">コード エディターで MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="f4eb0-125">呼び出しをコメント、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="f4eb0-126">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="f4eb0-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが既定のシステムのスタイルで描画します。</span><span class="sxs-lookup"><span data-stu-id="f4eb0-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4eb0-128">参照</span><span class="sxs-lookup"><span data-stu-id="f4eb0-128">See Also</span></span>  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f4eb0-129">visual スタイルが使用されているコントロールのレンダリング</span><span class="sxs-lookup"><span data-stu-id="f4eb0-129">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [<span data-ttu-id="f4eb0-130">チュートリアル: WPF での Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="f4eb0-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
