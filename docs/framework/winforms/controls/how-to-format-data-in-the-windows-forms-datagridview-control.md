---
title: '方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 7e3e281a766e22ed76bbf6ae7726cba092a9741d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538862"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2e3c5-102">方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="2e3c5-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2e3c5-103">次の手順の説明を使用してセル値の基本的な書式設定、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロールとコントロールの特定の列です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="2e3c5-104">高度なデータの書式設定方法の詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="2e3c5-105">通貨の書式設定および日付値</span><span class="sxs-lookup"><span data-stu-id="2e3c5-105">To format currency and date values</span></span>  
  
-   <span data-ttu-id="2e3c5-106"><xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="2e3c5-107">次のコード例を使用して特定の列の形式を設定する、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>列のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="2e3c5-108">値が、`UnitPrice`かっこで囲まれた負の値を持つ列が現在のカルチャに固有の通貨形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="2e3c5-109">値が、`ShipDate`列が、現在のカルチャに固有の短い日付形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="2e3c5-110">詳細については<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>値を参照してください[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="2e3c5-111">データベースの null 値の表示をカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="2e3c5-111">To customize the display of null database values</span></span>  
  
-   <span data-ttu-id="2e3c5-112"><xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="2e3c5-113">次のコード例では、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>と同じ値を含むすべてのセルに「エントリがありません」を表示するプロパティを<xref:System.DBNull.Value?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="2e3c5-114">セルのテキスト ベースのワード ラップを有効にするには</span><span class="sxs-lookup"><span data-stu-id="2e3c5-114">To enable wordwrap in text-based cells</span></span>  
  
-   <span data-ttu-id="2e3c5-115">設定、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>のいずれかに、<xref:System.Windows.Forms.DataGridViewTriState>列挙値。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="2e3c5-116">次のコード例では、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>コントロール全体のラップ モードを設定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="2e3c5-117">DataGridView セルのテキストの配置を指定するには</span><span class="sxs-lookup"><span data-stu-id="2e3c5-117">To specify the text alignment of DataGridView cells</span></span>  
  
-   <span data-ttu-id="2e3c5-118">設定、<xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>のいずれかに、<xref:System.Windows.Forms.DataGridViewContentAlignment>列挙値。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="2e3c5-119">次のコード例を使用して、特定の列の位置を設定する、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>列のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="2e3c5-120">例</span><span class="sxs-lookup"><span data-stu-id="2e3c5-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2e3c5-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2e3c5-121">Compiling the Code</span></span>  
 <span data-ttu-id="2e3c5-122">これらの例には次の項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-122">These examples require:</span></span>  
  
-   <span data-ttu-id="2e3c5-123">A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`dataGridView1`という名前の列を格納している`UnitPrice`、という名前の列`ShipDate`、という名前の列と`CustomerName`です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
-   <span data-ttu-id="2e3c5-124"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType>、および <xref:System.Windows.Forms?displayProperty=nameWithType> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2e3c5-125">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="2e3c5-125">Robust Programming</span></span>  
 <span data-ttu-id="2e3c5-126">スケーラビリティを最大にするには、共有する必要があります<xref:System.Windows.Forms.DataGridViewCellStyle>複数の行、列、または各要素のスタイル プロパティを個別に設定するのではなく、同じスタイルを使用するセルの間でのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="2e3c5-127">詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールを拡張するためのベスト プラクティス](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e3c5-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3c5-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e3c5-128">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="2e3c5-129">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="2e3c5-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="2e3c5-130">Windows フォーム DataGridView コントロールでのセルのスタイル</span><span class="sxs-lookup"><span data-stu-id="2e3c5-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="2e3c5-131">Windows フォーム DataGridView コントロールでのデータの書式設定</span><span class="sxs-lookup"><span data-stu-id="2e3c5-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="2e3c5-132">方法: Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="2e3c5-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="2e3c5-133">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="2e3c5-133">Formatting Types</span></span>](../../../../docs/standard/base-types/formatting-types.md)
