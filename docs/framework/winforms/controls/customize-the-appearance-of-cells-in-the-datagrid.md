---
title: "方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする"
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
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61b2a39943dfca412afa4b66265aabbf65b9ccf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3cb79-102">方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="3cb79-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3cb79-103">任意のセルの外観をカスタマイズするには、処理することにより、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellPainting>イベント。</span><span class="sxs-lookup"><span data-stu-id="3cb79-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="3cb79-104">抽出することができます、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Drawing.Graphics>から、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="3cb79-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="3cb79-105">この<xref:System.Drawing.Graphics>、全体の外観に影響する可能性<xref:System.Windows.Forms.DataGridView>コントロールは通常するのには現在塗りつぶされているセルの外観だけに影響します。</span><span class="sxs-lookup"><span data-stu-id="3cb79-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="3cb79-106"><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>現在塗りつぶされているセルに、描画操作を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="3cb79-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="3cb79-107">次のコード例では、すべてのセルを描画します、`ContactName`列を使用して、<xref:System.Windows.Forms.DataGridView>コントロールの色のスキーム。</span><span class="sxs-lookup"><span data-stu-id="3cb79-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="3cb79-108">各セルのテキスト コンテンツを描画する<xref:System.Drawing.Color.Crimson%2A>と同じ色に埋め込みの四角形を描画し、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.GridColor%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3cb79-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb79-109">例</span><span class="sxs-lookup"><span data-stu-id="3cb79-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cb79-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3cb79-110">Compiling the Code</span></span>  
 <span data-ttu-id="3cb79-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3cb79-111">This example requires:</span></span>  
  
-   <span data-ttu-id="3cb79-112">A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`dataGridView1`で、`ContactName`など、Northwind サンプル データベース内の Customers テーブルの列です。</span><span class="sxs-lookup"><span data-stu-id="3cb79-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="3cb79-113">System、System.Windows.Forms、および System.Drawing の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="3cb79-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb79-114">参照</span><span class="sxs-lookup"><span data-stu-id="3cb79-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [<span data-ttu-id="3cb79-115">Windows フォーム DataGridView コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="3cb79-115">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
