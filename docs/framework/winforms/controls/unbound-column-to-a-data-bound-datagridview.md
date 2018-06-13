---
title: '方法 : データバインドされた Windows フォーム DataGridView コントロールに非バインド列を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 8ba06457371bab5b81e18a307960a833d1d54199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537311"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="0ecdd-102">方法 : データバインドされた Windows フォーム DataGridView コントロールに非バインド列を追加する</span><span class="sxs-lookup"><span data-stu-id="0ecdd-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0ecdd-103"><xref:System.Windows.Forms.DataGridView> コントロールに表示するデータは、通常なんらかのデータ ソースから取得されるデータですが、データ ソース以外からのデータの列を表示する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="0ecdd-104">この種類の列は、非バインド列と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="0ecdd-105">非バインド列の形式はさまざまです。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="0ecdd-106">しばしば、データ行の詳細へのアクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="0ecdd-107">次のコード例は、の非バインド列を作成する方法を示します**詳細**マスター/詳細シナリオを実装するときに、親テーブルの特定の行に関連する子テーブルを表示するボタンです。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="0ecdd-108">ボタンのクリックに応答するには、子テーブルを含むフォームを表示する <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> イベント ハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="0ecdd-109">Visual Studio では、このタスクに対するサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="0ecdd-110">参照してください[する方法: 追加し、Windows フォーム DataGridView コントロールを使用して、デザイナーで列を削除します。](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0ecdd-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ecdd-111">例</span><span class="sxs-lookup"><span data-stu-id="0ecdd-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ecdd-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0ecdd-112">Compiling the Code</span></span>  
 <span data-ttu-id="0ecdd-113">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-113">This example requires:</span></span>  
  
-   <span data-ttu-id="0ecdd-114">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="0ecdd-115"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="0ecdd-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecdd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ecdd-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="0ecdd-117">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="0ecdd-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0ecdd-118">Windows フォーム DataGridView コントロールでのデータ表示モード</span><span class="sxs-lookup"><span data-stu-id="0ecdd-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
