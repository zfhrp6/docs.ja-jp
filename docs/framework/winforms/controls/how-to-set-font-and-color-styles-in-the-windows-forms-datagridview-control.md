---
title: "方法 : Windows フォーム DataGridView コントロールのフォントと色のスタイルを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb1c15be20775903a6fb7674660c552c464daab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8dbf9-102">方法 : Windows フォーム DataGridView コントロールのフォントと色のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="8dbf9-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8dbf9-103"><xref:System.Windows.Forms.DataGridViewCellStyle> クラスのプロパティを設定して、<xref:System.Windows.Forms.DataGridView> コントロール内のセルの外観を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="8dbf9-104"><xref:System.Windows.Forms.DataGridView> クラスとコンパニオン クラスのさまざまなプロパティからこのクラスのインスタンスを取得することも、これらのプロパティの割り当てに <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトをインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="8dbf9-105">次の手順は、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> プロパティを使用したセルの外観の基本的なカスタマイズを示します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="8dbf9-106">コントロール内のすべてのセルは、列、行、またはセル レベルでオーバーライドされるのでない限り、このプロパティで指定されたスタイルを継承します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="8dbf9-107">スタイルの継承の例は、次を参照してください。[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="8dbf9-108"><xref:System.Windows.Forms.DataGridViewCellStyle> クラスのその他の使用方法については、[参照] セクションの各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="8dbf9-109">Visual Studio では、このタスクに対する広範なサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="8dbf9-110">参照してください[する方法: 既定のセル スタイルの設定し、データ形式を Windows フォーム DataGridView コントロールを使用して、デザイナー](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="8dbf9-111">DataGridView セルで使用されるフォントを指定するには</span><span class="sxs-lookup"><span data-stu-id="8dbf9-111">To specify the font used by DataGridView cells</span></span>  
  
-   <span data-ttu-id="8dbf9-112"><xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="8dbf9-113">次のコード例では、コントロール全体のフォントを設定する <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="8dbf9-114">DataGridView セルの前景色と背景色を指定するには</span><span class="sxs-lookup"><span data-stu-id="8dbf9-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
-   <span data-ttu-id="8dbf9-115"><xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> プロパティと <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="8dbf9-116">次のコード例では、コントロール全体にこれらのスタイルを設定する <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="8dbf9-117">選択された DataGridView セルの前景色と背景色を指定するには</span><span class="sxs-lookup"><span data-stu-id="8dbf9-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
-   <span data-ttu-id="8dbf9-118"><xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> プロパティと <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="8dbf9-119">次のコード例では、コントロール全体にこれらのスタイルを設定する <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="8dbf9-120">例</span><span class="sxs-lookup"><span data-stu-id="8dbf9-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8dbf9-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8dbf9-121">Compiling the Code</span></span>  
 <span data-ttu-id="8dbf9-122">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-122">This example requires:</span></span>  
  
-   <span data-ttu-id="8dbf9-123">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="8dbf9-124"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType>、および <xref:System.Windows.Forms?displayProperty=nameWithType> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8dbf9-125">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="8dbf9-125">Robust Programming</span></span>  
 <span data-ttu-id="8dbf9-126">最大限のスケーラビリティを実現するには、各要素のスタイルのプロパティを個別に設定するのではなく、同じスタイルを使用する複数の行、列、またはセルで <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを共有してください。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="8dbf9-127">詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールを拡張するためのベスト プラクティス](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dbf9-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dbf9-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="8dbf9-128">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="8dbf9-129">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="8dbf9-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="8dbf9-130">Windows フォーム DataGridView コントロールでのセルのスタイル</span><span class="sxs-lookup"><span data-stu-id="8dbf9-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
