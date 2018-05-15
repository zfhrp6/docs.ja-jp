---
title: DataGridView コントロール (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: 3c642a2a0eccc5a2b08cee71ca719515b115b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="42a8a-102">DataGridView コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="42a8a-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="42a8a-103">`DataGridView` コントロールには、データを表形式で表示するための強力で柔軟な機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="42a8a-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="42a8a-104">`DataGridView` コントロールを使用すると、読み取り専用のビューに少量のデータを表示したり、拡大して非常に大量のデータのセットの編集可能なビューを表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="42a8a-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="42a8a-105">`DataGridView` コントロールはいくつかの方法で拡張でき、アプリケーションにカスタムの動作を組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="42a8a-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="42a8a-106">たとえば、プログラムで独自の並べ替えアルゴリズムを指定したり、独自の種類のセルを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="42a8a-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="42a8a-107">`DataGridView` コントロールの外観は、いくつかのプロパティを選択することで簡単にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="42a8a-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="42a8a-108">`DataGridView` コントロールでは、多くの種類のデータ ストアをデータ ソースとして使用できますが、データ ソースをバインドせずに動作させることもできます。</span><span class="sxs-lookup"><span data-stu-id="42a8a-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="42a8a-109">このセクションのトピックでは、`DataGridView` の機能をアプリケーションに組み込むときに使用できる概念および手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42a8a-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="42a8a-110">In This Section</span></span>  
 [<span data-ttu-id="42a8a-111">DataGridView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="42a8a-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="42a8a-112">Windows フォームの `DataGridView` コントロールのアーキテクチャおよび中心となる概念を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="42a8a-113">Windows フォーム DataGridView コントロールの既定の機能</span><span class="sxs-lookup"><span data-stu-id="42a8a-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-114">Windows フォームの `DataGridView` コントロールがデータ ソースにバインドされているときの既定の外観および動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="42a8a-115">Windows フォーム DataGridView コントロールの列型</span><span class="sxs-lookup"><span data-stu-id="42a8a-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-116">Windows フォームの `DataGridView` コントロールのデータの表示に使用する列型、およびユーザーがデータを変更または追加できるようにするために使用する列型について説明します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="42a8a-117">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="42a8a-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="42a8a-118">セル、行、および列の一般的なプロパティを説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="42a8a-119">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="42a8a-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-120">コントロールの基本の外観およびセル データの書式設定を変更する方法を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="42a8a-121">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="42a8a-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-122">コントロールに手動でデータを組み込む方法と、外部データ ソースからデータを取得する方法について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="42a8a-123">Windows フォーム DataGridView コントロール内の列と行のサイズ変更</span><span class="sxs-lookup"><span data-stu-id="42a8a-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-124">セルの内容に合わせて、またはコントロールが利用可能な幅に合わせて、行と列のサイズを自動的に調整する方法を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="42a8a-125">Windows フォームの DataGridView コントロールでのデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="42a8a-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-126">このコントロールの並べ替え機能について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="42a8a-127">Windows フォーム DataGridView コントロールでのデータ入力</span><span class="sxs-lookup"><span data-stu-id="42a8a-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-128">コントロールのデータに対してユーザーが実行できる追加および修正の仕方を変更する方法を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="42a8a-129">Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用</span><span class="sxs-lookup"><span data-stu-id="42a8a-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-130">コントロールのセル、行、および列の選択機能について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="42a8a-131">Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="42a8a-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="42a8a-132">セル、行、および列オブジェクトを使用したプログラミング方法を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="42a8a-133">Windows フォーム DataGridView コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="42a8a-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-134">`DataGridView` のセルおよび行のカスタム描画と、セル、列、および行の派生型の作成について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="42a8a-135">Windows フォーム DataGridView コントロールでのパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="42a8a-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-136">大量のデータを扱うときのパフォーマンスの問題を避けるために、このコントロールを効率的に使用する方法について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="42a8a-137">Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理</span><span class="sxs-lookup"><span data-stu-id="42a8a-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="42a8a-138">キーボードとマウスを介してユーザーが `DataGridView` コントロールとやり取りする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="42a8a-139">Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて</span><span class="sxs-lookup"><span data-stu-id="42a8a-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="42a8a-140">`DataGridView` コントロールが <xref:System.Windows.Forms.DataGrid> コントロールより改良され、これに代わるものである点について説明します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="42a8a-141">参照してください[デザイナーを使用して Windows フォーム DataGridView コントロールで](http://msdn.microsoft.com/library/ms171593\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="42a8a-141">Also see [Using the Designer with the Windows Forms DataGridView Control](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="42a8a-142">参照</span><span class="sxs-lookup"><span data-stu-id="42a8a-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="42a8a-143"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="42a8a-144"><xref:System.Windows.Forms.BindingSource> コンポーネントのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="42a8a-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="42a8a-145"><xref:System.Windows.Forms.DataGridView> コントロールと <xref:System.Windows.Forms.BindingSource> コンポーネントは、密接に連携して機能するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="42a8a-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a8a-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="42a8a-146">See Also</span></span>  
 [<span data-ttu-id="42a8a-147">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="42a8a-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
