---
title: '方法 : Windows フォームの DataGridView コントロールで列を読み取り専用にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 1ea4fdb6d38464993672c9aa98d8866812d21972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="eb7a0-102">方法 : Windows フォームの DataGridView コントロールで列を読み取り専用にする</span><span class="sxs-lookup"><span data-stu-id="eb7a0-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="eb7a0-103">すべてのデータが編集できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-103">Not all data is meant for editing.</span></span> <span data-ttu-id="eb7a0-104"><xref:System.Windows.Forms.DataGridView> コントロールでは、列の <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> プロパティの値はユーザーがその列のセルを編集できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="eb7a0-105">完全に読み取り専用のコントロールを作成する方法については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="eb7a0-106">Visual Studio では、このタスクに対するサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="eb7a0-107">参照してください[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで列読み取り専用のため](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="eb7a0-108">プログラムで列を読み取り専用にするには</span><span class="sxs-lookup"><span data-stu-id="eb7a0-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="eb7a0-109"><xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb7a0-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="eb7a0-110">Compiling the Code</span></span>  
 <span data-ttu-id="eb7a0-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-111">This example requires:</span></span>  
  
-   <span data-ttu-id="eb7a0-112">`CompanyName` という名前の列を持つ `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="eb7a0-113"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="eb7a0-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7a0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb7a0-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="eb7a0-115">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="eb7a0-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="eb7a0-116">方法: Windows フォーム DataGridView コントロールで行が追加および削除されないようにする</span><span class="sxs-lookup"><span data-stu-id="eb7a0-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
