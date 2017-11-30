---
title: "方法 : GridSplitter を使用して行のサイズを変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="e1490-102">方法 : GridSplitter を使用して行のサイズを変更する</span><span class="sxs-lookup"><span data-stu-id="e1490-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="e1490-103">この例は、水平方向の使用方法を示しています。<xref:System.Windows.Controls.GridSplitter>の 2 つの行の間の領域を再配布する、<xref:System.Windows.Controls.Grid>の寸法を変更することなく、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="e1490-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1490-104">例</span><span class="sxs-lookup"><span data-stu-id="e1490-104">Example</span></span>  
 <span data-ttu-id="e1490-105">**行の端に重なって表示される GridSplitter を作成する方法**</span><span class="sxs-lookup"><span data-stu-id="e1490-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="e1490-106">指定する、<xref:System.Windows.Controls.GridSplitter>で隣接する行のサイズを変更する、 <xref:System.Windows.Controls.Grid>、設定されて、<xref:System.Windows.Controls.Grid.Row%2A>のサイズを変更する行の 1 つにプロパティを接続します。</span><span class="sxs-lookup"><span data-stu-id="e1490-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="e1490-107">場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の列は、設定、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>添付プロパティの列の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1490-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="e1490-108">設定して、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に<xref:System.Windows.VerticalAlignment.Top>または<xref:System.Windows.VerticalAlignment.Bottom>(どの設定は整列する 2 つの行のサイズを変更する)。</span><span class="sxs-lookup"><span data-stu-id="e1490-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="e1490-109">最後に、設定、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Stretch>です。</span><span class="sxs-lookup"><span data-stu-id="e1490-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="e1490-110">次の例は、水平方向を定義する方法を示しています。<xref:System.Windows.Controls.GridSplitter>隣接する行のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="e1490-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="e1490-111">A<xref:System.Windows.Controls.GridSplitter>独自の行を占有しないで他のコントロールによって隠される可能性があります、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="e1490-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="e1490-112">この問題の詳しい回避方法については、[GridSplitter を表示されるようにする](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1490-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="e1490-113">**行を占有する GridSplitter を作成する方法**</span><span class="sxs-lookup"><span data-stu-id="e1490-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="e1490-114">指定する、<xref:System.Windows.Controls.GridSplitter>内の行を占有する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Row%2A>のサイズを変更する行の 1 つにプロパティを接続します。</span><span class="sxs-lookup"><span data-stu-id="e1490-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="e1490-115">場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の列は、設定、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>添付プロパティを列の数にします。</span><span class="sxs-lookup"><span data-stu-id="e1490-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="e1490-116">設定して、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に<xref:System.Windows.VerticalAlignment.Center>、設定されて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Stretch>、設定と、<xref:System.Windows.Controls.RowDefinition.Height%2A>を含む行の<xref:System.Windows.Controls.GridSplitter>に<xref:System.Windows.GridLength.Auto%2A>です。</span><span class="sxs-lookup"><span data-stu-id="e1490-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="e1490-117">次の例は、水平方向を定義する方法を示しています。<xref:System.Windows.Controls.GridSplitter>する行を占有し、その両側に行のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="e1490-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="e1490-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1490-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="e1490-119">データ バインドに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="e1490-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
