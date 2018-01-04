---
title: "方法 : Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする"
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
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1fd70aea1dec618a324d271d5bab34ac58ce85a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d91ce-102">方法 : Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="d91ce-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d91ce-103"><xref:System.Windows.Forms.DataGridView> コントロールは、自動並べ替え機能を提供しますが、ニーズに応じて、並べ替え操作をカスタマイズすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="d91ce-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="d91ce-104">たとえば、プログラムによる並べ替え機能を使用して、代替のユーザー インターフェイス (UI) を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d91ce-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="d91ce-105">また、複数の列の並べ替えなど、並べ替え柔軟性を高めるために、<xref:System.Windows.Forms.DataGridView.SortCompare> イベントを処理したり、<xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(IComparer)` のオーバーロードを呼び出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="d91ce-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="d91ce-106">次のコード例は、カスタムの並べ替えの 3 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d91ce-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="d91ce-107">詳細については、「[Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d91ce-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="d91ce-108">プログラムによる並べ替え</span><span class="sxs-lookup"><span data-stu-id="d91ce-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="d91ce-109">次のコード例は、<xref:System.Windows.Forms.DataGridView.SortOrder%2A> プロパティと <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> プロパティを使用して並べ替えの方向を判断し、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> プロパティを使用してナラベカエグリフを手動で設定する、プログラムによる並べ替えを示しています。</span><span class="sxs-lookup"><span data-stu-id="d91ce-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="d91ce-110"><xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(DataGridViewColumn,ListSortDirection)` のオーバーロードは 1 つの列のみでのデータの並べ替えに使用します。</span><span class="sxs-lookup"><span data-stu-id="d91ce-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="d91ce-111">SortCompare イベントを使用したカスタムの並べ替え</span><span class="sxs-lookup"><span data-stu-id="d91ce-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="d91ce-112">次のコード例は、<xref:System.Windows.Forms.DataGridView.SortCompare> イベント ハンドラーを使用したカスタムの並べ替えを示しています。</span><span class="sxs-lookup"><span data-stu-id="d91ce-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="d91ce-113">選択した <xref:System.Windows.Forms.DataGridViewColumn> が並べ替えられて、列に重複する値がある場合は、最終的な順序を決定する、ID 列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d91ce-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="d91ce-114">IComparer インターフェイスを使用したカスタムの並べ替え</span><span class="sxs-lookup"><span data-stu-id="d91ce-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="d91ce-115">次のコード例は、複数列の並べ替えを実行する <xref:System.Collections.IComparer> インターフェイスの実装を取得する <xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(IComparer)` のオーバーロードを使用したカスタムの並べ替えを示しています。</span><span class="sxs-lookup"><span data-stu-id="d91ce-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d91ce-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d91ce-116">Compiling the Code</span></span>  
 <span data-ttu-id="d91ce-117">これらの例には次の項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="d91ce-117">These examples require:</span></span>  
  
-   <span data-ttu-id="d91ce-118">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="d91ce-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d91ce-119">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d91ce-119">For information about building these examples from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d91ce-120">また、コードを新しいプロジェクトに貼り付けることにより、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d91ce-120">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="d91ce-121">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="d91ce-121">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d91ce-122">参照</span><span class="sxs-lookup"><span data-stu-id="d91ce-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="d91ce-123">Windows フォームの DataGridView コントロールでのデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="d91ce-123">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d91ce-124">Windows フォーム DataGridView コントロール内の列の並べ替えモード</span><span class="sxs-lookup"><span data-stu-id="d91ce-124">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d91ce-125">方法: Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する</span><span class="sxs-lookup"><span data-stu-id="d91ce-125">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
