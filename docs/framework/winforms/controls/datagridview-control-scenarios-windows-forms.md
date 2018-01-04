---
title: "DataGridView コントロールのシナリオ (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38e5337f775d98f8729c62b3481c3e839bff2252
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a><span data-ttu-id="86892-102">DataGridView コントロールのシナリオ (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="86892-102">DataGridView Control Scenarios (Windows Forms)</span></span>
<span data-ttu-id="86892-103"><xref:System.Windows.Forms.DataGridView>コントロール、さまざまなデータ ソースから表形式のデータを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-103">With the <xref:System.Windows.Forms.DataGridView> control, you can display tabular data from a variety of data sources.</span></span> <span data-ttu-id="86892-104">単純な使用方法については、手動で設定できる、<xref:System.Windows.Forms.DataGridView>コントロールから直接データを操作します。</span><span class="sxs-lookup"><span data-stu-id="86892-104">For simple uses, you can manually populate a <xref:System.Windows.Forms.DataGridView> and manipulate the data directly through the control.</span></span> <span data-ttu-id="86892-105">通常、ただし、外部データ ソースにデータを格納してコントロールをバインドして、<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="86892-105">Typically, however, you will store your data in an external data source and bind the control to it through a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="86892-106">このトピックでは、いくつかを実行する一般的なシナリオについて説明します、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="86892-106">This topic describes some of the common scenarios that involve the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a><span data-ttu-id="86892-107">シナリオ 1: 少量のデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="86892-107">Scenario 1: Displaying Small Amounts of Data</span></span>  
 <span data-ttu-id="86892-108">表示する外部データ ソースにデータを格納する必要はありません、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="86892-108">You do not have to store your data in an external data source to display it in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="86892-109">少量のデータを扱う場合は、コントロールを設定し、コントロールからデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="86892-109">If you are working with a small amount of data, you can populate the control yourself and manipulate the data through the control.</span></span> <span data-ttu-id="86892-110">これと呼ばれる*バインドされていないモード*です。</span><span class="sxs-lookup"><span data-stu-id="86892-110">This is called *unbound mode*.</span></span> <span data-ttu-id="86892-111">詳細については、次を参照してください。[する方法: バインドされていない Windows フォームの DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-111">For more information, see [How to: Create an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="86892-112">シナリオの要点</span><span class="sxs-lookup"><span data-stu-id="86892-112">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="86892-113">モードではバインドされていない、設定コントロール手動でします。</span><span class="sxs-lookup"><span data-stu-id="86892-113">In unbound mode, you populate the control manually.</span></span>  
  
-   <span data-ttu-id="86892-114">バインドされていないモードは、読み取り専用データが少ない場合に特に適しています。</span><span class="sxs-lookup"><span data-stu-id="86892-114">Unbound mode is particularly suited for small amounts of read-only data.</span></span>  
  
-   <span data-ttu-id="86892-115">バインドされていないモードはスプレッドシート形式または付けますテーブルにも適しています。</span><span class="sxs-lookup"><span data-stu-id="86892-115">Unbound mode is also suited for spreadsheet-like or sparsely populated tables.</span></span>  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a><span data-ttu-id="86892-116">シナリオ 2: 表示して、外部データ ソースに格納されているデータの更新</span><span class="sxs-lookup"><span data-stu-id="86892-116">Scenario 2: Viewing and Updating Data Stored in an External Data Source</span></span>  
 <span data-ttu-id="86892-117">使用することができます、<xref:System.Windows.Forms.DataGridView>ユーザーから、データベース テーブルまたはビジネス オブジェクトのコレクションなどのデータ ソースに保持されるデータにアクセスできるユーザー インターフェイス (UI) を管理します。</span><span class="sxs-lookup"><span data-stu-id="86892-117">You can use the <xref:System.Windows.Forms.DataGridView> control as a user interface (UI) through which users can access data kept in a data source such as a database table or a collection of business objects.</span></span> <span data-ttu-id="86892-118">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールにデータをバインド](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-118">For more information, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="86892-119">シナリオの要点</span><span class="sxs-lookup"><span data-stu-id="86892-119">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="86892-120">バインドされたモードでは、データ ソースへの接続、データ ソースのプロパティまたはデータベース列に基づく列を自動的に生成し、コントロールを自動的に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-120">Bound mode lets you connect to a data source, automatically generate columns based on the data source properties or database columns, and automatically populate the control.</span></span>  
  
-   <span data-ttu-id="86892-121">バインド モードは、ユーザー負荷が高いデータが操作に適しています。</span><span class="sxs-lookup"><span data-stu-id="86892-121">Bound mode is suited for heavy user interaction with data.</span></span> <span data-ttu-id="86892-122">データを表示する形式指定できるし、ユーザー指定のデータは、データ ソースによって予期される形式に解析できます。</span><span class="sxs-lookup"><span data-stu-id="86892-122">Data can be formatted for display, and user-specified data can be parsed into the format expected by the data source.</span></span> <span data-ttu-id="86892-123">ユーザーに警告され、該当するセルを修正できるように、データ エントリ エラーおよびデータベースの制約のエラーの書式設定を検出できます。</span><span class="sxs-lookup"><span data-stu-id="86892-123">Data entry formatting errors and database constraint errors can be detected so that users can be warned and erroneous cells can be corrected.</span></span>  
  
-   <span data-ttu-id="86892-124">列の並べ替えなどの追加機能は、固定すること、および並べ替えは、ワークフローに最も便利な方法でデータを表示するユーザーに有効にします。</span><span class="sxs-lookup"><span data-stu-id="86892-124">Additional functionality such as column sorting, freezing, and reordering enable users to view data in the way most convenient for their workflow.</span></span>  
  
-   <span data-ttu-id="86892-125">クリップボードのサポートでは、他のアプリケーションにアプリケーションからデータをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="86892-125">Clipboard support enables users to copy data from your application into other applications.</span></span>  
  
## <a name="scenario-3-advanced-data"></a><span data-ttu-id="86892-126">シナリオ 3: 高度なデータ</span><span class="sxs-lookup"><span data-stu-id="86892-126">Scenario 3: Advanced Data</span></span>  
 <span data-ttu-id="86892-127">実装することによってコントロールとデータ間の相互作用を管理するには、標準的なデータ バインディング モデルでは取り上げません特別なニーズがあれば、*仮想モード*です。</span><span class="sxs-lookup"><span data-stu-id="86892-127">If you have special needs that the standard data binding model does not address, you can manage the interaction between the control and your data by implementing *virtual mode*.</span></span> <span data-ttu-id="86892-128">セルに関する情報と、コントロール要求情報ことのできる 1 つまたは複数のイベント ハンドラーの実装の仮想モード手段を実装することが必要です。</span><span class="sxs-lookup"><span data-stu-id="86892-128">Implementing virtual mode means implementing one or more event handlers that let the control request information about cells as the information is needed.</span></span>  
  
 <span data-ttu-id="86892-129">たとえば、大量のデータを操作する場合、最適な効率性を確保する仮想モードを実装します。</span><span class="sxs-lookup"><span data-stu-id="86892-129">For example, if you work with large amounts of data, you may want to implement virtual mode to ensure optimal efficiency.</span></span> <span data-ttu-id="86892-130">仮想モードも別のデータ ソースから取得した列と共に表示する非バインド列の値を維持するため便利です。</span><span class="sxs-lookup"><span data-stu-id="86892-130">Virtual mode is also useful for maintaining the values of unbound columns that you display along with columns retrieved from another data source.</span></span>  
  
 <span data-ttu-id="86892-131">仮想モードの詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-131">For more information about virtual mode, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="86892-132">シナリオの要点</span><span class="sxs-lookup"><span data-stu-id="86892-132">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="86892-133">仮想モードは、パフォーマンスを微調整する必要がある場合は、非常に大量のデータを表示するために適しています。</span><span class="sxs-lookup"><span data-stu-id="86892-133">Virtual mode is suited for displaying very large amounts of data when you need to fine-tune performance.</span></span>  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a><span data-ttu-id="86892-134">シナリオ 4: は、行と列に自動的にサイズ変更</span><span class="sxs-lookup"><span data-stu-id="86892-134">Scenario 4: Automatically Resizing Rows and Columns</span></span>  
 <span data-ttu-id="86892-135">定期的に更新されるデータを表示するときに自動的にサイズを変更する行と列のすべてのコンテンツが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="86892-135">When you display data that is regularly updated, you can automatically resize rows and columns to ensure that all content is visible.</span></span> <span data-ttu-id="86892-136"><xref:System.Windows.Forms.DataGridView>コントロールには、有効または無効にする手動によるサイズ変更、特定の時刻では、プログラムでのサイズを変更するのに便利ないくつかのオプションが用意されていますか、自動的にサイズ変更されるたびに、変更をコンテンツします。</span><span class="sxs-lookup"><span data-stu-id="86892-136">The <xref:System.Windows.Forms.DataGridView> control provides several options that let you enable or disable manual resizing, resize programmatically at specific times, or resize automatically whenever content changes.</span></span> <span data-ttu-id="86892-137">詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-137">For more information, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="86892-138">シナリオの要点</span><span class="sxs-lookup"><span data-stu-id="86892-138">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="86892-139">手動のサイズを変更すると、セルの高さと幅を調整するユーザーができます。</span><span class="sxs-lookup"><span data-stu-id="86892-139">Manual resizing enables users to adjust cell heights and widths.</span></span>  
  
-   <span data-ttu-id="86892-140">自動サイズ変更するには、セルの内容がクリップされないように、セルのサイズを維持することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-140">Automatic resizing enables you to maintain cell sizes so that cell content is never clipped.</span></span>  
  
-   <span data-ttu-id="86892-141">プログラムによるサイズ変更するには、継続的なサイズの自動調整のパフォーマンスの低下を避けるために特定の時点でのセルのサイズを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-141">Programmatic resizing enables you to resize cells at specific times to avoid the performance penalty of continuous automatic resizing.</span></span>  
  
## <a name="scenario-5-simple-customization"></a><span data-ttu-id="86892-142">シナリオ 5: 単純なカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="86892-142">Scenario 5: Simple Customization</span></span>  
 <span data-ttu-id="86892-143"><xref:System.Windows.Forms.DataGridView>コントロールには、その基本的な外観と動作を変更するためのさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="86892-143">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to alter its basic appearance and behavior.</span></span> <span data-ttu-id="86892-144">詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのセル スタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-144">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="86892-145">シナリオの要点</span><span class="sxs-lookup"><span data-stu-id="86892-145">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="86892-146"><xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクトを使用して、色、フォント、書式設定、および複数のレベルと、コントロールの個々 の要素の位置情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="86892-146"><xref:System.Windows.Forms.DataGridViewCellStyle> objects let you provide color, font, formatting, and positioning information at multiple levels and for individual elements of the control.</span></span>  
  
-   <span data-ttu-id="86892-147">セル スタイルは、レイヤーし、コードを再利用すること、複数の要素で共有されることができます。</span><span class="sxs-lookup"><span data-stu-id="86892-147">Cell styles can be layered and shared by multiple elements, letting you reuse code.</span></span>  
  
## <a name="scenario-6-advanced-customization"></a><span data-ttu-id="86892-148">シナリオ 6: 高度なカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="86892-148">Scenario 6: Advanced Customization</span></span>  
 <span data-ttu-id="86892-149"><xref:System.Windows.Forms.DataGridView>コントロールには、外観や動作をカスタマイズするためのさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="86892-149">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to customize its appearance and behavior.</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="86892-150">シナリオの要点</span><span class="sxs-lookup"><span data-stu-id="86892-150">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="86892-151">セルの描画コードを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-151">You can provide your own cell painting code.</span></span> <span data-ttu-id="86892-152">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-152">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="86892-153">独自の行のペイントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="86892-153">You can provide your own row painting.</span></span> <span data-ttu-id="86892-154">たとえば、コンテンツにまたがる複数の列を含む行を作成するこれは、便利です。</span><span class="sxs-lookup"><span data-stu-id="86892-154">This is useful, for example, to create rows with content that spans multiple columns.</span></span> <span data-ttu-id="86892-155">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで行の外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-155">For more information, see [How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="86892-156">セルの外観をカスタマイズする、独自のセルと列のクラスを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-156">You can implement your own cell and column classes to customize cell appearance.</span></span> <span data-ttu-id="86892-157">詳細については、次を参照してください。[する方法: セルのカスタマイズおよびその動作を拡張すると外観が Windows フォーム DataGridView コントロールで列](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-157">For more information, see [How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).</span></span>  
  
-   <span data-ttu-id="86892-158">組み込み列の型によって提供されるもの以外のホスト コントロールを独自のセルと列のクラスを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="86892-158">You can implement your own cell and column classes to host controls other than the ones provided by the built-in column types.</span></span> <span data-ttu-id="86892-159">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView セルでホスト コントロール](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)です。</span><span class="sxs-lookup"><span data-stu-id="86892-159">For more information, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86892-160">参照</span><span class="sxs-lookup"><span data-stu-id="86892-160">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="86892-161">DataGridView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="86892-161">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
