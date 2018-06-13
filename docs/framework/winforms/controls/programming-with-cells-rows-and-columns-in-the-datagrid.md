---
title: Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], elements
- columns [Windows Forms], data grids
- cells [Windows Forms], data grids
- DataGridView control [Windows Forms], programming with grid elements
- rows [Windows Forms], data grids
ms.assetid: 0d76f7e4-4149-42c6-9118-bb37d6669dc5
ms.openlocfilehash: f87d1e2744ffcd81f5711991880deb1fe5edd2a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538542"
---
# <a name="programming-with-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="352b2-102">Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="352b2-102">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="352b2-103">このセクションでは、セル、行、および列オブジェクトに関連するさまざまなプログラミング タスクについて説明するトピックを提供します。</span><span class="sxs-lookup"><span data-stu-id="352b2-103">This section provides topics that demonstrate various programming tasks involving cell, row, and column objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="352b2-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="352b2-104">In This Section</span></span>  
 [<span data-ttu-id="352b2-105">方法: Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する</span><span class="sxs-lookup"><span data-stu-id="352b2-105">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/add-tooltips-to-individual-cells-in-a-wf-datagridview-control.md)  
 <span data-ttu-id="352b2-106">処理する方法について説明します、<xref:System.Windows.Forms.DataGridView.CellFormatting>個々 のセルを別のツール ヒントを提供するイベントです。</span><span class="sxs-lookup"><span data-stu-id="352b2-106">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting> event to provide different ToolTips for individual cells.</span></span>  
  
 [<span data-ttu-id="352b2-107">方法: Windows フォーム DataGridView コントロールのセルの変更に基づいてカスタム動作を実行する</span><span class="sxs-lookup"><span data-stu-id="352b2-107">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/perform-a-custom-action-based-on-changes-in-a-cell-of-a-datagrid.md)  
 <span data-ttu-id="352b2-108">処理する方法について説明します、<xref:System.Windows.Forms.DataGridView.CellValueChanged>と<xref:System.Windows.Forms.DataGridView.CellStateChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="352b2-108">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
 [<span data-ttu-id="352b2-109">方法: Windows フォームの DataGridView コントロールのバンドを操作する</span><span class="sxs-lookup"><span data-stu-id="352b2-109">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-bands-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="352b2-110">型のオブジェクトのプログラミング方法について説明<xref:System.Windows.Forms.DataGridViewBand>、これは行と列の基本型です。</span><span class="sxs-lookup"><span data-stu-id="352b2-110">Describes how to program with objects of type <xref:System.Windows.Forms.DataGridViewBand>, which is the base type for rows and columns.</span></span>  
  
 [<span data-ttu-id="352b2-111">方法: Windows フォームの DataGridView コントロールの行を操作する</span><span class="sxs-lookup"><span data-stu-id="352b2-111">How to: Manipulate Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="352b2-112">型のオブジェクトのプログラミング方法について説明`DataGridViewRow`です。</span><span class="sxs-lookup"><span data-stu-id="352b2-112">Describes how to program with objects of type `DataGridViewRow`.</span></span>  
  
 [<span data-ttu-id="352b2-113">方法: Windows フォーム DataGridView コントロールの列を操作する</span><span class="sxs-lookup"><span data-stu-id="352b2-113">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="352b2-114">型のオブジェクトのプログラミング方法について説明`DataGridViewColumn`です。</span><span class="sxs-lookup"><span data-stu-id="352b2-114">Describes how to program with objects of type `DataGridViewColumn`.</span></span>  
  
 [<span data-ttu-id="352b2-115">方法: Windows フォーム DataGridView コントロールのイメージ列を操作する</span><span class="sxs-lookup"><span data-stu-id="352b2-115">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="352b2-116">使用したプログラミング方法について説明します、`DataGridViewImageColumn`クラスです。</span><span class="sxs-lookup"><span data-stu-id="352b2-116">Describes how to program with the `DataGridViewImageColumn` class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="352b2-117">参照</span><span class="sxs-lookup"><span data-stu-id="352b2-117">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="352b2-118"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="352b2-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="352b2-119">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewCell>クラスです。</span><span class="sxs-lookup"><span data-stu-id="352b2-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="352b2-120">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewRow>クラスです。</span><span class="sxs-lookup"><span data-stu-id="352b2-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="352b2-121">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumn>クラスです。</span><span class="sxs-lookup"><span data-stu-id="352b2-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="352b2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="352b2-122">Related Sections</span></span>  
 [<span data-ttu-id="352b2-123">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="352b2-123">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="352b2-124">よくを説明するトピックに使用されるセル、行、および列のプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="352b2-124">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352b2-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="352b2-125">See Also</span></span>  
 [<span data-ttu-id="352b2-126">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="352b2-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="352b2-127">Windows フォーム DataGridView コントロールの列型</span><span class="sxs-lookup"><span data-stu-id="352b2-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
