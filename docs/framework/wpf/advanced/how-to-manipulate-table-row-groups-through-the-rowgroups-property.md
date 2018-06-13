---
title: '方法: テーブルを操作&#39;s 行グループ、行グループのプロパティ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 8cdf3b74fa5bf5a566c541ba035a1c7da7dd6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545166"
---
# <a name="how-to-manipulate-a-table39s-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="df685-102">方法: テーブルを操作&#39;s 行グループ、行グループのプロパティ</span><span class="sxs-lookup"><span data-stu-id="df685-102">How to: Manipulate a Table&#39;s Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="df685-103">この例を使用して、テーブルの行グループで実行できる一般的な操作の一部を示しています、<xref:System.Windows.Documents.Table.RowGroups%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="df685-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df685-104">例</span><span class="sxs-lookup"><span data-stu-id="df685-104">Example</span></span>  
 <span data-ttu-id="df685-105">次の例は、新しいテーブルを作成し、使用、<xref:System.Windows.Documents.TableRowGroupCollection.Add%2A>テーブルの列を追加するメソッドを<xref:System.Windows.Documents.Table.RowGroups%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="df685-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="df685-106">例</span><span class="sxs-lookup"><span data-stu-id="df685-106">Example</span></span>  
 <span data-ttu-id="df685-107">次の例は、新しい挿入<xref:System.Windows.Documents.TableRowGroup>です。</span><span class="sxs-lookup"><span data-stu-id="df685-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="df685-108">新しい最初の行を行うインデックス位置 0 の場合に、新しい列が挿入されるテーブルのグループ化します。</span><span class="sxs-lookup"><span data-stu-id="df685-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df685-109"><xref:System.Windows.Documents.TableRowGroupCollection>コレクションで標準の 0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="df685-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="df685-110">例</span><span class="sxs-lookup"><span data-stu-id="df685-110">Example</span></span>  
 <span data-ttu-id="df685-111">次の例では、いくつかの行を追加する特定の<xref:System.Windows.Documents.TableRowGroup>(インデックスによって指定された) テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="df685-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="df685-112">例</span><span class="sxs-lookup"><span data-stu-id="df685-112">Example</span></span>  
 <span data-ttu-id="df685-113">次の例では、テーブル内の最初の行グループ内の行での任意のプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="df685-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="df685-114">例</span><span class="sxs-lookup"><span data-stu-id="df685-114">Example</span></span>  
 <span data-ttu-id="df685-115">次の例では、複数のセルを追加する特定の<xref:System.Windows.Documents.TableRow>(インデックスによって指定された) テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="df685-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="df685-116">例</span><span class="sxs-lookup"><span data-stu-id="df685-116">Example</span></span>  
 <span data-ttu-id="df685-117">次の例は、いくつかの任意のメソッドと最初の行グループの最初の行のセルのプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="df685-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="df685-118">例</span><span class="sxs-lookup"><span data-stu-id="df685-118">Example</span></span>  
 <span data-ttu-id="df685-119">次の例の数を返します<xref:System.Windows.Documents.TableRowGroup>テーブルによってホストされている要素です。</span><span class="sxs-lookup"><span data-stu-id="df685-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="df685-120">例</span><span class="sxs-lookup"><span data-stu-id="df685-120">Example</span></span>  
 <span data-ttu-id="df685-121">次の例は、参照によって、特定の行グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="df685-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="df685-122">例</span><span class="sxs-lookup"><span data-stu-id="df685-122">Example</span></span>  
 <span data-ttu-id="df685-123">次の例では、インデックスを使用して特定の行グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="df685-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="df685-124">例</span><span class="sxs-lookup"><span data-stu-id="df685-124">Example</span></span>  
 <span data-ttu-id="df685-125">次の例では、テーブルの行グループのコレクションからすべての行グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="df685-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="df685-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="df685-126">See Also</span></span>  
 [<span data-ttu-id="df685-127">方法: 操作のインライン プロパティを介してフロー コンテンツ要素</span><span class="sxs-lookup"><span data-stu-id="df685-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="df685-128">Blocks プロパティを介して FlowDocument を操作する</span><span class="sxs-lookup"><span data-stu-id="df685-128">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="df685-129">Columns プロパティによってテーブルの列を操作する</span><span class="sxs-lookup"><span data-stu-id="df685-129">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
