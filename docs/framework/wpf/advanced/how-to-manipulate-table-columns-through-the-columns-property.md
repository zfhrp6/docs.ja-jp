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
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a>方法: テーブルを操作&#39;列プロパティを通じて s 列
この例では、によって、テーブルの列で実行できる一般的な操作の一部を示しています、<xref:System.Windows.Documents.Table.Columns%2A>プロパティです。  
  
## <a name="example"></a>例  
 次の例は、新しいテーブルを作成し、使用、<xref:System.Windows.Documents.TableColumnCollection.Add%2A>テーブルの列を追加するメソッドを<xref:System.Windows.Documents.Table.Columns%2A>コレクション。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>例  
 次の例は、新しい挿入<xref:System.Windows.Documents.TableColumn>です。  インデックス位置 0 の場合の表に、新しい最初の列を行うには、新しい列が挿入されます。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableColumnCollection>コレクションで標準の 0 から始まるインデックスを使用します。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>例  
 次の例では、任意のプロパティ内の列に、<xref:System.Windows.Documents.TableColumnCollection>インデックスを使用して特定の列を参照するコレクション。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>例  
 次の例では、テーブルによって現在ホストされている列の数を取得します。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>例  
 次の例では、参照によって、特定の列を削除します。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>例  
 次の例では、インデックスを使用して、特定の列を削除します。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>例  
 次の例では、テーブルの列のコレクションからすべての列を削除します。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>関連項目  
 [テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [XAML を使用してテーブルを定義する](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [プログラムによってテーブルをビルドする](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
