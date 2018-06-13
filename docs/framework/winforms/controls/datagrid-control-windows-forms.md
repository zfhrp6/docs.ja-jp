---
title: DataGrid コントロール (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: 8618bfc691e86e8c609a6205ab44a891cc7e9f80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529952"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="686aa-102">DataGrid コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="686aa-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="686aa-103"><xref:System.Windows.Forms.DataGridView> コントロールは、`DataGrid` コントロールに代わると共に追加の機能を提供します。ただし、`DataGrid` コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="686aa-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="686aa-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="686aa-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="686aa-105">Windows フォームの `DataGrid` コントロールは、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] データセットへのユーザー インターフェイスを提供し、データを表形式で表示して、データ ソースを更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="686aa-105">The Windows Forms `DataGrid` control provides a user interface to [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="686aa-106">`DataGrid` コントロールを有効なデータ ソースに対して設定すると、データの形式に基づいて列と行が作成されたコントロールが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="686aa-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="686aa-107">`DataGrid` コントロールを使用すると、1 つのテーブルまたは、複数のテーブル間の階層的なリレーションシップを表示できます。</span><span class="sxs-lookup"><span data-stu-id="686aa-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="686aa-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="686aa-108">In This Section</span></span>  
 [<span data-ttu-id="686aa-109">DataGrid コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="686aa-109">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="686aa-110">`DataGrid` コントロールの基本機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-111">方法 : デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する</span><span class="sxs-lookup"><span data-stu-id="686aa-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="686aa-112">デザイナーを使用して `DataGrid` コントロールにテーブルと列を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="686aa-113">方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する</span><span class="sxs-lookup"><span data-stu-id="686aa-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="686aa-114">プログラムによって `DataGrid` コントロールにテーブルと列を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="686aa-115">方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="686aa-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="686aa-116">デザイナーを使用して [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] データセットを `DataGrid` コントロールにバインドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-116">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="686aa-117">方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="686aa-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="686aa-118">[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] データセットを `DataGrid` コントロールにバインドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-118">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-119">方法 : Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する</span><span class="sxs-lookup"><span data-stu-id="686aa-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="686aa-120">`DataGrid` コントロール内でプログラムによってデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-121">方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する</span><span class="sxs-lookup"><span data-stu-id="686aa-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="686aa-122">デザイナーを使用して、親子のリレーションシップで結合されている 2 つのテーブルを、2 つの `DataGrid` コントロールに個別に表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="686aa-123">方法 : Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する</span><span class="sxs-lookup"><span data-stu-id="686aa-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="686aa-124">親子のリレーションシップで結合されている 2 つのテーブルを、2 つの `DataGrid` コントロールに個別に表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="686aa-125">方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする</span><span class="sxs-lookup"><span data-stu-id="686aa-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="686aa-126">`DataGrid` コントロール内で列を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-127">方法 : デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="686aa-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="686aa-128">デザイナーを使用して、`DataGrid` コントロールの外観に関連するプロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="686aa-129">方法 : Windows フォーム DataGrid コントロールの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="686aa-129">How to: Format the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="686aa-130">`DataGrid` コントロールの外観に関連するプロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-131">Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="686aa-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="686aa-132">`DataGrid` コントロール内の移動に使用できるキーボード ショートカットの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="686aa-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-133">方法 : Windows フォーム DataGrid コントロールのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="686aa-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="686aa-134">ユーザーがクリックした `DataGrid` コントロール内のセルを確認する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="686aa-135">方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する</span><span class="sxs-lookup"><span data-stu-id="686aa-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="686aa-136">`DataGrid` コントロールにバインドされたデータセット内の入力データを検証する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="686aa-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="686aa-137">参照</span><span class="sxs-lookup"><span data-stu-id="686aa-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="686aa-138">概要を示します、<xref:System.Windows.Forms.DataGrid>クラスです。</span><span class="sxs-lookup"><span data-stu-id="686aa-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="686aa-139">このプロパティを使用してバインドする方法の詳細を提供、<xref:System.Windows.Forms.DataGrid>コントロールをデータにします。</span><span class="sxs-lookup"><span data-stu-id="686aa-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="686aa-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="686aa-140">Related Sections</span></span>  
 [<span data-ttu-id="686aa-141">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="686aa-141">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="686aa-142">Windows フォームのデータ結合に関するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="686aa-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686aa-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="686aa-143">See Also</span></span>  
 [<span data-ttu-id="686aa-144">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="686aa-144">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="686aa-145">Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて</span><span class="sxs-lookup"><span data-stu-id="686aa-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
