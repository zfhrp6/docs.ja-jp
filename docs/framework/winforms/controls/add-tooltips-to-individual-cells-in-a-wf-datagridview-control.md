---
title: '方法 : Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: 50eb02a8f6e9a987fad074c173ab6711fa91143f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527701"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="4adbd-102">方法 : Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する</span><span class="sxs-lookup"><span data-stu-id="4adbd-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4adbd-103">既定では、ツールヒントを使用しての値を表示する<xref:System.Windows.Forms.DataGridView>セルが全体の内容を表示するには小さすぎることです。</span><span class="sxs-lookup"><span data-stu-id="4adbd-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="4adbd-104">ただし、この動作をオーバーライドする個々 のセルのツールヒントのテキスト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="4adbd-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="4adbd-105">これは、セルに関する追加情報をユーザーに表示するか、セルの内容の他の説明をユーザーに提供するには便利です。</span><span class="sxs-lookup"><span data-stu-id="4adbd-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="4adbd-106">たとえば、状態アイコンを表示する行がある場合は、場合、ツールヒントを使用して説明を提供します。</span><span class="sxs-lookup"><span data-stu-id="4adbd-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="4adbd-107">設定してセル レベルのツールヒントの表示を無効にすることも、<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="4adbd-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="4adbd-108">セルにツールヒントを追加するには</span><span class="sxs-lookup"><span data-stu-id="4adbd-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="4adbd-109"><xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4adbd-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4adbd-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="4adbd-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4adbd-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4adbd-111">This example requires:</span></span>  
  
-   <span data-ttu-id="4adbd-112">A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`dataGridView1`という名前の列を格納している`Rating`4 つのアスタリスクを 1 つの文字列値を表示する ("\*") シンボル。</span><span class="sxs-lookup"><span data-stu-id="4adbd-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="4adbd-113"><xref:System.Windows.Forms.DataGridView.CellFormatting>の例に示すようにイベント ハンドラー メソッドを使用して、コントロールのイベントを関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4adbd-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="4adbd-114"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="4adbd-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4adbd-115">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="4adbd-115">Robust Programming</span></span>  
 <span data-ttu-id="4adbd-116">バインドすると、<xref:System.Windows.Forms.DataGridView>外部データ ソースを制御または仮想モードを実装することで、独自のデータ ソースを提供、パフォーマンスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4adbd-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="4adbd-117">パフォーマンスの低下を避けるためには、大量のデータを操作するとき、処理、<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>設定ではなく、イベント、<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>複数のセルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="4adbd-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="4adbd-118">ときにこのイベントを処理、セルの値を取得する<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>プロパティは、イベントを発生させるしの値を返します、<xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>としてプロパティを指定のイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="4adbd-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adbd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4adbd-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4adbd-120">Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="4adbd-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
