---
title: "方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する"
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
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a31bfc6fb3fa8a3c549a10fd0db017abde66539f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="56d48-102">方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する</span><span class="sxs-lookup"><span data-stu-id="56d48-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="56d48-103"><xref:System.Windows.Forms.DataGridView>コントロール、コントロールの枠線と、ユーザー エクスペリエンスを向上させるためにグリッド線の外観をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="56d48-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="56d48-104">グリッド線の色と、コントロール内のセルの境界線スタイルに加え、コントロールの境界線のスタイルを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="56d48-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="56d48-105">通常のセル、行ヘッダー セル、および列ヘッダー セルの別のセルの境界線のスタイルを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="56d48-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56d48-106">グリッド線の色でのみ使用、 <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>、 <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>、および<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical>の値、<xref:System.Windows.Forms.DataGridViewCellBorderStyle>列挙と<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single>の値、<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>列挙します。</span><span class="sxs-lookup"><span data-stu-id="56d48-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="56d48-107">これらの列挙体の他の値は、オペレーティング システムによって指定された色を使用します。</span><span class="sxs-lookup"><span data-stu-id="56d48-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="56d48-108">さらに、visual スタイルが有効な場合に Windows XP および Windows Server 2003 ファミリを<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>、メソッド、<xref:System.Windows.Forms.DataGridView.GridColor%2A>プロパティの値は使用されません。</span><span class="sxs-lookup"><span data-stu-id="56d48-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="56d48-109">グリッド線の色をプログラムで変更するには</span><span class="sxs-lookup"><span data-stu-id="56d48-109">To change the gridline color programmatically</span></span>  
  
-   <span data-ttu-id="56d48-110"><xref:System.Windows.Forms.DataGridView.GridColor%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="56d48-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="56d48-111">全体の DataGridView コントロールの境界線スタイルをプログラムで変更するには</span><span class="sxs-lookup"><span data-stu-id="56d48-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
-   <span data-ttu-id="56d48-112"><xref:System.Windows.Forms.DataGridView.BorderStyle%2A> プロパティを <xref:System.Windows.Forms.BorderStyle> 列挙値のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="56d48-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="56d48-113">DataGridView セルの境界線のスタイルをプログラムで変更するには</span><span class="sxs-lookup"><span data-stu-id="56d48-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
-   <span data-ttu-id="56d48-114">設定、 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>、 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>、および<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="56d48-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="56d48-115">例</span><span class="sxs-lookup"><span data-stu-id="56d48-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56d48-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="56d48-116">Compiling the Code</span></span>  
 <span data-ttu-id="56d48-117">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="56d48-117">This example requires:</span></span>  
  
-   <span data-ttu-id="56d48-118">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="56d48-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="56d48-119"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、および <xref:System.Drawing?displayProperty=nameWithType> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="56d48-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d48-120">参照</span><span class="sxs-lookup"><span data-stu-id="56d48-120">See Also</span></span>  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [<span data-ttu-id="56d48-121">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="56d48-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
