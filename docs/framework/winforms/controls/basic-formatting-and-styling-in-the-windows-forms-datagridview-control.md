---
title: Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d38620c321fb12b9f489fd086e222b7780337ab3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528796"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="db603-102">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="db603-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="db603-103">`DataGridView`コントロールでは、簡単にセルの基本の外観およびセルの値の表示形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="db603-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="db603-104">外観を定義することができ、個々 のセル、行、および特定の列にセルまたはコントロールのすべてのセルのプロパティを設定してスタイルの書式設定、`DataGridViewCellStyle`さまざまなを介してアクセスされるオブジェクト`DataGridView`プロパティを制御します。</span><span class="sxs-lookup"><span data-stu-id="db603-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="db603-105">さらに、処理することにより、セルの値などの要因に基づいて動的にこれらのスタイルを変更することができます、`CellFormatting`イベント。</span><span class="sxs-lookup"><span data-stu-id="db603-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db603-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="db603-106">In This Section</span></span>  
 [<span data-ttu-id="db603-107">方法: Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する</span><span class="sxs-lookup"><span data-stu-id="db603-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="db603-108">設定する方法について説明`DataGridView`コントロールの境界線とセル間の境界線の外観を定義するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="db603-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="db603-109">Windows フォーム DataGridView コントロールでのセルのスタイル</span><span class="sxs-lookup"><span data-stu-id="db603-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db603-110">について説明します、`DataGridViewCellStyle`クラス対話方法とその型のプロパティをコントロールにセルを表示する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="db603-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="db603-111">方法: Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="db603-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db603-112">使用する方法について説明`DataGridViewCellStyle`特定の行と列では、コントロール全体では、セルの既定の外観を定義するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="db603-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="db603-113">方法: Windows フォーム DataGridView コントロールのデータの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="db603-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db603-114">使用して、セルの表示値の書式を設定する方法について説明`DataGridViewCellStyle`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="db603-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="db603-115">方法: Windows フォーム DataGridView コントロールのフォントと色のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="db603-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db603-116">使用する方法について説明します、`DefaultCellStyle`基本的な設定するプロパティがコントロールにすべてのセルの特性を表示します。</span><span class="sxs-lookup"><span data-stu-id="db603-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="db603-117">方法: Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="db603-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db603-118">異なる方法で表示される交互の行を使用して、コントロールで、帳簿のような効果を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db603-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="db603-119">方法: 行テンプレートを使用して Windows フォーム DataGridView コントロールの行をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="db603-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="db603-120">使用する方法について説明します、`RowTemplate`プロパティをすべての行のコントロールで使用される行のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="db603-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db603-121">参照</span><span class="sxs-lookup"><span data-stu-id="db603-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="db603-122"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="db603-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="db603-123">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスです。</span><span class="sxs-lookup"><span data-stu-id="db603-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="db603-124">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。</span><span class="sxs-lookup"><span data-stu-id="db603-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="db603-125">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="db603-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="db603-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="db603-126">Related Sections</span></span>  
 [<span data-ttu-id="db603-127">Windows フォーム DataGridView コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="db603-127">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db603-128"><xref:System.Windows.Forms.DataGridView> のセルおよび行のカスタム描画と、セル、列、および行の派生型の作成について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="db603-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="db603-129">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="db603-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="db603-130">よくを説明するトピックに使用されるセル、行、および列のプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="db603-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db603-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="db603-131">See Also</span></span>  
 [<span data-ttu-id="db603-132">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="db603-132">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
