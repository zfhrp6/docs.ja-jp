---
title: "方法 : GridSplitter を使用して列のサイズを変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d68d829e5543b1c299668493c11b62ccb11d81af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="a48e3-102">方法 : GridSplitter を使用して列のサイズを変更する</span><span class="sxs-lookup"><span data-stu-id="a48e3-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="a48e3-103">この例は、垂直方向を作成する方法を示します<xref:System.Windows.Controls.GridSplitter>で 2 つの列間のスペースを再配布するために、<xref:System.Windows.Controls.Grid>の寸法を変更することがなく、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="a48e3-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a48e3-104">例</span><span class="sxs-lookup"><span data-stu-id="a48e3-104">Example</span></span>  
 <span data-ttu-id="a48e3-105">**列の端に重なって表示される GridSplitter を作成する方法**</span><span class="sxs-lookup"><span data-stu-id="a48e3-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="a48e3-106">指定する、<xref:System.Windows.Controls.GridSplitter>内の隣接する列のサイズを変更する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Column%2A>にサイズを変更する列の 1 つの添付プロパティ。</span><span class="sxs-lookup"><span data-stu-id="a48e3-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="a48e3-107">場合、 <xref:System.Windows.Controls.Grid> 1 つ以上の行がある設定、<xref:System.Windows.Controls.Grid.RowSpan%2A>行の数にプロパティをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="a48e3-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="a48e3-108">設定して、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Left>または<xref:System.Windows.HorizontalAlignment.Right>(どの設定は整列する 2 つの列のサイズを変更する)。</span><span class="sxs-lookup"><span data-stu-id="a48e3-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="a48e3-109">最後に、設定、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.VerticalAlignment.Stretch>です。</span><span class="sxs-lookup"><span data-stu-id="a48e3-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="a48e3-110">A<xref:System.Windows.Controls.GridSplitter>独自の列を持たない他のコントロールによって隠される可能性があります、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="a48e3-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="a48e3-111">この問題の詳しい回避方法については、[GridSplitter を表示されるようにする](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a48e3-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="a48e3-112">**列を占有する GridSplitter を作成する方法**</span><span class="sxs-lookup"><span data-stu-id="a48e3-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="a48e3-113">指定する、<xref:System.Windows.Controls.GridSplitter>内の列を占有する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Column%2A>にサイズを変更する列の 1 つの添付プロパティ。</span><span class="sxs-lookup"><span data-stu-id="a48e3-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="a48e3-114">グリッドに複数の行がある場合は、設定、<xref:System.Windows.Controls.Grid.RowSpan%2A>行の数にプロパティをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="a48e3-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="a48e3-115">設定して、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>に<xref:System.Windows.HorizontalAlignment.Center>、設定されて、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.VerticalAlignment.Stretch>、設定と、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>を含む列の<xref:System.Windows.Controls.GridSplitter>に<xref:System.Windows.GridLength.Auto%2A>です。</span><span class="sxs-lookup"><span data-stu-id="a48e3-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="a48e3-116">次の例は、垂直方向を定義する方法を示しています。<xref:System.Windows.Controls.GridSplitter>する列を占有し、そのいずれかの側の列のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="a48e3-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="a48e3-117">参照</span><span class="sxs-lookup"><span data-stu-id="a48e3-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="a48e3-118">データ バインドに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="a48e3-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
