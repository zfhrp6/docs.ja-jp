---
title: '方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 08d90bb45006af798b629f58821cbf50ee9ef089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="77dc8-102">方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する</span><span class="sxs-lookup"><span data-stu-id="77dc8-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="77dc8-103"><xref:System.Windows.Forms.DataGridView>他の列の型が自動的に並べ替えられていないときに、既定では、自動並べ替えコントロール、テキスト ボックスの列を使用します。</span><span class="sxs-lookup"><span data-stu-id="77dc8-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="77dc8-104">これらの既定値をオーバーライドする場合があります。</span><span class="sxs-lookup"><span data-stu-id="77dc8-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="77dc8-105">たとえば、テキスト、数値、または列挙型のセルの値の代わりにイメージを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="77dc8-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="77dc8-106">イメージを並べ替えることはできません、中に、それが表す基になる値を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="77dc8-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="77dc8-107"><xref:System.Windows.Forms.DataGridView>コントロール、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>列のプロパティの値の並べ替えの動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="77dc8-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="77dc8-108">次の手順に示します、`Priority`から列[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="77dc8-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="77dc8-109">この列は image 列であり、既定では並べ替えられません。</span><span class="sxs-lookup"><span data-stu-id="77dc8-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="77dc8-110">自動的に並べ替えることができますので、ただし、文字列の場合は、実際のセル値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="77dc8-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="77dc8-111">列の並べ替えモードを設定するには</span><span class="sxs-lookup"><span data-stu-id="77dc8-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="77dc8-112"><xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="77dc8-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77dc8-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="77dc8-113">Compiling the Code</span></span>  
 <span data-ttu-id="77dc8-114">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="77dc8-114">This example requires:</span></span>  
  
-   <span data-ttu-id="77dc8-115">`Priority` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="77dc8-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="77dc8-116"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="77dc8-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77dc8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="77dc8-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="77dc8-118">Windows フォームの DataGridView コントロールでのデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="77dc8-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="77dc8-119">Windows フォーム DataGridView コントロール内の列の並べ替えモード</span><span class="sxs-lookup"><span data-stu-id="77dc8-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="77dc8-120">方法: Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="77dc8-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
