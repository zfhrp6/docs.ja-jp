---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65f876742526d13093a852e99f4e6a069c3fba47
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="af7d6-102">方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する</span><span class="sxs-lookup"><span data-stu-id="af7d6-102">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="af7d6-103"><xref:System.Windows.Forms.DataGridView>コントロールを使用する既定のセル スタイルを指定し、コントロール全体の特定の列に対して、行ヘッダーおよび列ヘッダー、および交互の行台帳効果を作成するデータ形式します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-103">The <xref:System.Windows.Forms.DataGridView> control lets you specify default cell styles and cell data formats for the entire control, for specific columns, for row and column headers, and for alternating rows to create a ledger effect.</span></span> <span data-ttu-id="af7d6-104">コントロール全体の設定の既定のスタイルは、既定のスタイルが交互の行と列設定によって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="af7d6-104">Default styles set for the entire control are overridden by default styles set for columns and alternating rows.</span></span> <span data-ttu-id="af7d6-105">さらに、個々 の行とセルのコードに設定するスタイルは、既定のスタイルをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="af7d6-105">Additionally, styles that you set in code for individual rows and cells override the default styles.</span></span>  
  
 <span data-ttu-id="af7d6-106">セルのスタイルの詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのセル スタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-106">For more information about cell styles, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="af7d6-107">交互の行のスタイルを設定するを参照してください。[する方法: 交互の行のスタイルを Windows フォーム DataGridView コントロールを使用して、デザイナー設定](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-107">To set styles for alternating rows, see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="af7d6-108">使用してスタイルを設定することも、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティをコントロールに追加されるすべての行に影響します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-108">You can also set styles using the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property to affect all rows that will be added to the control.</span></span> <span data-ttu-id="af7d6-109">行テンプレートの詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで行のカスタマイズ、行テンプレートを使用して](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-109">For more information about the row template, see [How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).</span></span>  
  
 <span data-ttu-id="af7d6-110">次の手順が必要な**Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="af7d6-110">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="af7d6-111">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af7d6-112">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="af7d6-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="af7d6-113">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af7d6-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="af7d6-114">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af7d6-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a><span data-ttu-id="af7d6-115">コントロール内のすべてのセルの既定のスタイルを設定するには</span><span class="sxs-lookup"><span data-stu-id="af7d6-115">To set default styles for all cells in the control</span></span>  
  
1.  <span data-ttu-id="af7d6-116">選択、<xref:System.Windows.Forms.DataGridView>デザイナーで制御します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-116">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>  
  
2.  <span data-ttu-id="af7d6-117">**プロパティ**ウィンドウで、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>、または<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="af7d6-117">In the **Properties** window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> property.</span></span> <span data-ttu-id="af7d6-118">**CellStyle ビルダー**  ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="af7d6-118">The **CellStyle Builder** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="af7d6-119">使用してプロパティを設定してスタイルを定義、**プレビュー**ウィンドウ選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-119">Define the style by setting the properties, using the **Preview** pane to confirm your choices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af7d6-120">Visual スタイルが有効な場合、行および列ヘッダー (以外の<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) が自動的には、現在のテーマでスタイルをオーバーライドする、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティの値。</span><span class="sxs-lookup"><span data-stu-id="af7d6-120">If visual styles are enabled, the row and column headers (except for the <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) are automatically styled by the current theme, overriding the <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> property values.</span></span>  
>   
>  <span data-ttu-id="af7d6-121">選択された複数のセル スタイルを設定することができます<xref:System.Windows.Forms.DataGridView>セル スタイル プロパティを変更するのと同じ値がある場合にのみ、デザイナーの使用を制御します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-121">You can set cell styles for multiple selected <xref:System.Windows.Forms.DataGridView> controls using the designer, but only if they have identical values for the cell style property you want to modify.</span></span> <span data-ttu-id="af7d6-122">そのプロパティの任意のセルのスタイルが異なる場合、**プロパティ**の windows、 **CellStyle ビルダー**  ダイアログ ボックスは空白になります。</span><span class="sxs-lookup"><span data-stu-id="af7d6-122">If any cell styles differ for that property, the **Properties** windows of the **CellStyle Builder** dialog box will be blank.</span></span>  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a><span data-ttu-id="af7d6-123">個々 の列のセルの既定のスタイルを設定するには</span><span class="sxs-lookup"><span data-stu-id="af7d6-123">To set default styles for cells in individual columns</span></span>  
  
1.  <span data-ttu-id="af7d6-124">右クリックし、<xref:System.Windows.Forms.DataGridView>デザイナーで制御し、選択**列の編集**です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-124">Right-click the <xref:System.Windows.Forms.DataGridView> control in the designer and choose **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="af7d6-125">列を選択して、**選択されている列** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-125">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="af7d6-126">**列のプロパティ**グリッドで、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>プロパティ。</span><span class="sxs-lookup"><span data-stu-id="af7d6-126">In the **Column Properties** grid, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="af7d6-127">**CellStyle ビルダー**  ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="af7d6-127">The **CellStyle Builder** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="af7d6-128">使用してプロパティを設定してスタイルを定義、**プレビュー**ウィンドウ選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-128">Define the style by setting the properties, using the **Preview** pane to confirm your choices.</span></span>  
  
### <a name="to-format-data-in-cells"></a><span data-ttu-id="af7d6-129">セル内のデータの書式を設定するには</span><span class="sxs-lookup"><span data-stu-id="af7d6-129">To format data in cells</span></span>  
  
1.  <span data-ttu-id="af7d6-130">使用して、前述の手順のいずれかを表示、 **CellStyle ビルダー**  ダイアログ ボックスが既定のセル スタイル プロパティに関連します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-130">Use one of the preceding procedures to display a **CellStyle Builder** dialog box related to a default cell style property.</span></span>  
  
2.  <span data-ttu-id="af7d6-131">**CellStyle ビルダー**  ダイアログ ボックスで、省略記号ボタンをクリックして (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>プロパティ。</span><span class="sxs-lookup"><span data-stu-id="af7d6-131">In the **CellStyle Builder** dialog box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property.</span></span> <span data-ttu-id="af7d6-132">**書式指定文字列** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="af7d6-132">The **Format String** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="af7d6-133">形式の種類を選択し、表示する小数点以下桁数の数) などの型の詳細の変更を使用して、**サンプル**ボックス選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="af7d6-133">Select a format type, then modify the details of the type (such as the number of decimal places to display), using the **Sample** box to confirm your choices.</span></span>  
  
4.  <span data-ttu-id="af7d6-134">バインドする場合、<xref:System.Windows.Forms.DataGridView>によって null 値を含む、入力がデータ ソースへのコントロール、 **Null 値**テキスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="af7d6-134">If you are binding the <xref:System.Windows.Forms.DataGridView> control to a data source that is likely to contain null values, fill in the **Null Value** text box.</span></span> <span data-ttu-id="af7d6-135">セルの値が null 参照に等しい場合に、この値が表示されます (`Nothing` Visual basic) または<xref:System.DBNull.Value?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="af7d6-135">This value is displayed when the cell value is equal to a null reference (`Nothing` in Visual Basic) or <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7d6-136">参照</span><span class="sxs-lookup"><span data-stu-id="af7d6-136">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="af7d6-137">Windows フォーム DataGridView コントロールでのセルのスタイル</span><span class="sxs-lookup"><span data-stu-id="af7d6-137">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="af7d6-138">方法: デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="af7d6-138">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="af7d6-139">方法: Windows アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="af7d6-139">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="af7d6-140">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="af7d6-140">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
