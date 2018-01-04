---
title: "方法 : Windows フォーム DataGridView コントロールの選択されたセル、行、および列を取得する"
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
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22b44668b403b5a991c03de661b6e680ccde0a44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1bba8-102">方法 : Windows フォーム DataGridView コントロールの選択されたセル、行、および列を取得する</span><span class="sxs-lookup"><span data-stu-id="1bba8-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1bba8-103">選択したセル、行、または列を取得することができます、<xref:System.Windows.Forms.DataGridView>対応するプロパティを使用して制御: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>、および<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>です。</span><span class="sxs-lookup"><span data-stu-id="1bba8-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="1bba8-104">次の手順では、選択したセルを取得しでその行と列のインデックスを表示、<xref:System.Windows.Forms.MessageBox>です。</span><span class="sxs-lookup"><span data-stu-id="1bba8-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="1bba8-105">DataGridView コントロールで選択したセルを取得するには</span><span class="sxs-lookup"><span data-stu-id="1bba8-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="1bba8-106"><xref:System.Windows.Forms.DataGridView.SelectedCells%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="1bba8-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1bba8-107">使用して、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>メソッド可能性のある多数のセルが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="1bba8-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="1bba8-108">DataGridView コントロールで選択した行を取得するには</span><span class="sxs-lookup"><span data-stu-id="1bba8-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="1bba8-109"><xref:System.Windows.Forms.DataGridView.SelectedRows%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="1bba8-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="1bba8-110">行を選択するユーザーを有効にするを設定する必要があります、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティを<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>です。</span><span class="sxs-lookup"><span data-stu-id="1bba8-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="1bba8-111">DataGridView コントロールで選択した列を取得するには</span><span class="sxs-lookup"><span data-stu-id="1bba8-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="1bba8-112"><xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="1bba8-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="1bba8-113">列を選択するユーザーを有効にするを設定する必要があります、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティを<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>です。</span><span class="sxs-lookup"><span data-stu-id="1bba8-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bba8-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1bba8-114">Compiling the Code</span></span>  
 <span data-ttu-id="1bba8-115">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1bba8-115">This example requires:</span></span>  
  
-   <span data-ttu-id="1bba8-116"><xref:System.Windows.Forms.Button>という名前のコントロール`selectedCellsButton`、 `selectedRowsButton`、および`selectedColumnsButton`、それぞれのハンドラーが、<xref:System.Windows.Forms.Control.Click>添付イベント。</span><span class="sxs-lookup"><span data-stu-id="1bba8-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="1bba8-117">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="1bba8-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="1bba8-118"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、および <xref:System.Text?displayProperty=nameWithType> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="1bba8-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1bba8-119">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="1bba8-119">Robust Programming</span></span>  
 <span data-ttu-id="1bba8-120">このトピックで説明するコレクションを実行しません効率的に多数のセル、行、または列を選択した場合。</span><span class="sxs-lookup"><span data-stu-id="1bba8-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="1bba8-121">大量のデータをこれらのコレクションを使用する方法の詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールを拡張するためのベスト プラクティス](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="1bba8-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bba8-122">参照</span><span class="sxs-lookup"><span data-stu-id="1bba8-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>  
 [<span data-ttu-id="1bba8-123">Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用</span><span class="sxs-lookup"><span data-stu-id="1bba8-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
