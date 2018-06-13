---
title: '方法: テーブルを操作&#39;列プロパティを通じて s 列'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: 916764c621738ddc651580f1232e1f579a17e6f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545299"
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a><span data-ttu-id="74a6c-102">方法: テーブルを操作&#39;列プロパティを通じて s 列</span><span class="sxs-lookup"><span data-stu-id="74a6c-102">How to: Manipulate a Table&#39;s Columns through the Columns Property</span></span>
<span data-ttu-id="74a6c-103">この例では、によって、テーブルの列で実行できる一般的な操作の一部を示しています、<xref:System.Windows.Documents.Table.Columns%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="74a6c-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74a6c-104">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-104">Example</span></span>  
 <span data-ttu-id="74a6c-105">次の例は、新しいテーブルを作成し、使用、<xref:System.Windows.Documents.TableColumnCollection.Add%2A>テーブルの列を追加するメソッドを<xref:System.Windows.Documents.Table.Columns%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="74a6c-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="74a6c-106">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-106">Example</span></span>  
 <span data-ttu-id="74a6c-107">次の例は、新しい挿入<xref:System.Windows.Documents.TableColumn>です。</span><span class="sxs-lookup"><span data-stu-id="74a6c-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="74a6c-108">インデックス位置 0 の場合の表に、新しい最初の列を行うには、新しい列が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="74a6c-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74a6c-109"><xref:System.Windows.Documents.TableColumnCollection>コレクションで標準の 0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="74a6c-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="74a6c-110">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-110">Example</span></span>  
 <span data-ttu-id="74a6c-111">次の例では、任意のプロパティ内の列に、<xref:System.Windows.Documents.TableColumnCollection>インデックスを使用して特定の列を参照するコレクション。</span><span class="sxs-lookup"><span data-stu-id="74a6c-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="74a6c-112">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-112">Example</span></span>  
 <span data-ttu-id="74a6c-113">次の例では、テーブルによって現在ホストされている列の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="74a6c-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="74a6c-114">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-114">Example</span></span>  
 <span data-ttu-id="74a6c-115">次の例では、参照によって、特定の列を削除します。</span><span class="sxs-lookup"><span data-stu-id="74a6c-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="74a6c-116">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-116">Example</span></span>  
 <span data-ttu-id="74a6c-117">次の例では、インデックスを使用して、特定の列を削除します。</span><span class="sxs-lookup"><span data-stu-id="74a6c-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="74a6c-118">例</span><span class="sxs-lookup"><span data-stu-id="74a6c-118">Example</span></span>  
 <span data-ttu-id="74a6c-119">次の例では、テーブルの列のコレクションからすべての列を削除します。</span><span class="sxs-lookup"><span data-stu-id="74a6c-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="74a6c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="74a6c-120">See Also</span></span>  
 [<span data-ttu-id="74a6c-121">テーブルの概要</span><span class="sxs-lookup"><span data-stu-id="74a6c-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [<span data-ttu-id="74a6c-122">XAML を使用してテーブルを定義する</span><span class="sxs-lookup"><span data-stu-id="74a6c-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="74a6c-123">プログラムによってテーブルをビルドする</span><span class="sxs-lookup"><span data-stu-id="74a6c-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [<span data-ttu-id="74a6c-124">RowGroups プロパティを介してテーブルの行グループを操作する</span><span class="sxs-lookup"><span data-stu-id="74a6c-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="74a6c-125">Blocks プロパティを介して FlowDocument を操作する</span><span class="sxs-lookup"><span data-stu-id="74a6c-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="74a6c-126">RowGroups プロパティを介してテーブルの行グループを操作する</span><span class="sxs-lookup"><span data-stu-id="74a6c-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
