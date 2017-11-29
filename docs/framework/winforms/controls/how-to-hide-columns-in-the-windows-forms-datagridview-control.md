---
title: "方法 : Windows フォームの DataGridView コントロールの列を非表示にする"
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
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4c0dd32e6d0633a18d18905992d5defbe838923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="82c85-102">方法 : Windows フォームの DataGridView コントロールの列を非表示にする</span><span class="sxs-lookup"><span data-stu-id="82c85-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="82c85-103">Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールで使用できる列の一部のみを表示したいときがあります。</span><span class="sxs-lookup"><span data-stu-id="82c85-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="82c85-104">たとえば、管理の資格情報を持つユーザーには従業員の給与の列を表示し、その他のユーザーには非表示にしたいときがあります。</span><span class="sxs-lookup"><span data-stu-id="82c85-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="82c85-105">また、多数の列を含み、その一部のみを表示したいデータ ソースにコントロールをバインドすることもあります。</span><span class="sxs-lookup"><span data-stu-id="82c85-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="82c85-106">この場合、通常は列を非表示にするよりは、必要がない列を削除します。</span><span class="sxs-lookup"><span data-stu-id="82c85-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="82c85-107"><xref:System.Windows.Forms.DataGridView> コントロールでは、列の <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> プロパティの値により、その列が表示されているかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="82c85-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="82c85-108">Visual Studio では、このタスクに対するサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="82c85-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="82c85-109">参照してください[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで列を非表示に](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="82c85-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="82c85-110">プログラムで列を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="82c85-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="82c85-111"><xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="82c85-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="82c85-112">データのバインド中に自動的に生成された `CustomerID` 列を非表示にするには、<xref:System.Windows.Forms.DataGridView.DataBindingComplete> イベント ハンドラーに次のコードの列を配置します。</span><span class="sxs-lookup"><span data-stu-id="82c85-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82c85-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="82c85-113">Compiling the Code</span></span>  
 <span data-ttu-id="82c85-114">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="82c85-114">This example requires:</span></span>  
  
-   <span data-ttu-id="82c85-115">`CustomerID` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="82c85-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="82c85-116"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="82c85-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c85-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="82c85-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="82c85-118">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="82c85-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="82c85-119">方法: Windows フォーム DataGridView コントロールから自動生成された列を削除する</span><span class="sxs-lookup"><span data-stu-id="82c85-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="82c85-120">方法: Windows フォーム DataGridView コントロールの列の順序を変更する</span><span class="sxs-lookup"><span data-stu-id="82c85-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
