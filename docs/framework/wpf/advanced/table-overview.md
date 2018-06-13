---
title: テーブルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 631a14ae8eb17713186f7db66700026cc476024e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549371"
---
# <a name="table-overview"></a>テーブルの概要
<xref:System.Windows.Documents.Table> グリッド ベース フロー ドキュメントの内容の表示形式をサポートするブロック レベル要素です。 この要素は、その柔軟性により非常に便利ですが、正しく理解して使用するのが難しいとも言えます。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [テーブルの基本](#table_basics)  
  
-   [テーブルとグリッドの相違点](#table_vs_Grid)  
  
-   [テーブルの基本構造](#basic_table_structure)  
  
-   [テーブルの内容](#table_containment)  
  
-   [行グループ](#row_groupings)  
  
-   [背景のレンダリングの優先順位](#rendering_precedence)  
  
-   [複数の行または列にまたがるセル](#spanning_rows_or_columns)  
  
-   [テーブルとコードのバインディング](#building_a_table_with_code)  
  
-   関連トピック 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>テーブルの基本  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>テーブルとグリッドの相違点  
 <xref:System.Windows.Documents.Table> および<xref:System.Windows.Controls.Grid>各はさまざまなシナリオに最適なはいくつかの一般的な機能を共有します。 A<xref:System.Windows.Documents.Table>フロー コンテンツ内で使用するために設計されていますが (を参照してください[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)フロー コンテンツの詳細については)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 内で、 <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Table>サポート フロー コンテンツの動作などの改ページ、列の折り返し、およびコンテンツの選択中に、<xref:System.Windows.Controls.Grid>しません。 A<xref:System.Windows.Controls.Grid>一方は最適以外で使用される、<xref:System.Windows.Documents.FlowDocument>さまざまな理由<xref:System.Windows.Controls.Grid>行と列のインデックスに基づいて要素を追加<xref:System.Windows.Documents.Table>しません。 <xref:System.Windows.Controls.Grid>要素により、1 つの「セル」内に存在する 1 つ以上の要素を許可する子コンテンツの重ね順 <xref:System.Windows.Documents.Table> 重ね順をサポートしていません。 子要素、 <xref:System.Windows.Controls.Grid> 「セル」境界外部の領域と相対的絶対位置に配置できます。 <xref:System.Windows.Documents.Table> この機能はサポートしません。 最後に、<xref:System.Windows.Controls.Grid>少ないリソースを必要とし、<xref:System.Windows.Documents.Table>ので使用を検討して、<xref:System.Windows.Controls.Grid>パフォーマンスを向上させるためにします。  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>テーブルの基本構造  
 <xref:System.Windows.Documents.Table> 列から成るグリッド ベースのプレゼンテーションを提供 (によって表される<xref:System.Windows.Documents.TableColumn>要素) と行 (によって表される<xref:System.Windows.Documents.TableRow>要素)。 <xref:System.Windows.Documents.TableColumn> 要素は、コンテンツをホストしていません。単に列と列の特性を定義します。 <xref:System.Windows.Documents.TableRow> 要素でホストされる必要があります、<xref:System.Windows.Documents.TableRowGroup>要素は、テーブルの行のグループを定義します。 <xref:System.Windows.Documents.TableCell> テーブルに表示する実際のコンテンツが含まれる要素をホストする必要があります、<xref:System.Windows.Documents.TableRow>要素。 <xref:System.Windows.Documents.TableCell> 派生した要素のみを含めることが<xref:System.Windows.Documents.Block>です。  有効な子要素、<xref:System.Windows.Documents.TableCell>が含まれます。  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> 要素は、テキスト コンテンツを直接ホスト可能性があります。 などの要素のコンテンツ フローの包含規則の詳細については<xref:System.Windows.Documents.TableCell>を参照してください[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)です。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> に似ていますが、<xref:System.Windows.Controls.Grid>要素が、多くの機能があり、したがって、大きいリソースのオーバーヘッドが必要です。  
  
 次の例では、単純な 2 x 3 テーブル[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]です。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 基本的なテーブルの描画] (../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>テーブルの内容  
 <xref:System.Windows.Documents.Table> 派生した、<xref:System.Windows.Documents.Block>要素の一般的な規則に準拠している<xref:System.Windows.Documents.Block>レベルの要素。  A<xref:System.Windows.Documents.Table>要素は、次の要素のいずれかが含まれる可能性があります。  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>行グループ  
 <xref:System.Windows.Documents.TableRowGroup>要素がテーブル内の行を任意にグループ化する方法を提供します。 テーブル内のすべての行が行グループに属する必要があります。  多くの場合、行グループ内の行は共通の目的を共有しており、1 つのグループとしてスタイルを設定できます。  一般に、行のグループ化は、テーブルに格納された主要コンテンツから、特別な目的を持つ行 (タイトル行、ヘッダー行、フッター行など) を分離するために使用します。  
  
 次の例で[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]スタイル設定されたヘッダーとフッター行を含むテーブルを定義します。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: テーブル行グループ] (../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>背景のレンダリングの優先順位  
 テーブル要素は、次の順序でレンダリングされます (優先順位の低い項目から高い項目の z オーダー)。 この順序は変更できません。 たとえば、これらの要素には、確立された順序をオーバーライドするための "Z オーダー" プロパティは用意されていません。  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 テーブル内のこれらの各要素に対して背景色を定義する例を次に示します。  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 次の図は、この例の表示結果 (背景色のみ表示) を示したものです。  
  
 ![スクリーンショット: テーブル z オーダー] (../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>複数の行または列にまたがるセル  
 テーブルのセルを使用して複数の行または列にまたがるように構成できます、<xref:System.Windows.Documents.TableCell.RowSpan%2A>または<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>属性をそれぞれします。  
  
 3 つの列にまたがるセルの例を次に示します。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 3 つの列すべてにまたがるセル] (../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>テーブルとコードのバインディング  
 次の例は、プログラムで作成する方法を示して、<xref:System.Windows.Documents.Table>し、コンテンツを設定します。 テーブルの内容は、5 つの行に分配する (によって表される<xref:System.Windows.Documents.TableRow>に含まれるオブジェクト、<xref:System.Windows.Documents.Table.RowGroups%2A>オブジェクト) と 6 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>オブジェクト)。 たとえば、タイトル行はテーブル全体のタイトルの設定に使用され、ヘッダー行はテーブル内のデータ列の説明、フッター行は要約情報の格納に使用されます。  "タイトル"、"ヘッダー"、"フッター" 行の概念はテーブルに固有のものではなく、単純に異なる特性を持つ行です。 テキスト、画像、またはその他のほとんどので構成されることができます、実際のコンテンツを含むテーブル セルが[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]要素。  
  
 最初に、<xref:System.Windows.Documents.FlowDocument>が作成されるホストに、 <xref:System.Windows.Documents.Table>、され、新しい<xref:System.Windows.Documents.Table>が作成され、コンテンツの追加、<xref:System.Windows.Documents.FlowDocument>です。  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 次に、6<xref:System.Windows.Documents.TableColumn>オブジェクトが作成され、テーブルに追加された<xref:System.Windows.Documents.Table.Columns%2A>コレクション、書式を適用します。  
  
> [!NOTE]
>  なお、テーブルの<xref:System.Windows.Documents.Table.Columns%2A>コレクションで標準の 0 から始まるインデックスを使用します。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 次に、タイトル行を作成してテーブルに追加し、書式を適用します。  タイトル行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 次に、ヘッダー行を作成してテーブルに追加し、ヘッダー行のセルを作成してデータを格納します。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 次に、データ行を作成してテーブルに追加し、この行のセルを作成してデータを格納します。  この行の作成はヘッダー行の作成に似ていますが、適用する書式が少し異なります。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後に、フッター行を作成して追加し、書式を設定します。  タイトル行と同様に、フッター行にはテーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>関連項目  
 [フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [XAML を使用してテーブルを定義する](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [フロー コンテンツ要素を使用する](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
