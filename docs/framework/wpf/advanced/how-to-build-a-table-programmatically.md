---
title: "方法 : プログラムによってテーブルをビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "作成, テーブル (プログラムを使用)"
  - "ドキュメント, プログラムで作成 (テーブルを)"
  - "テーブル, 作成 (プログラムによる)"
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : プログラムによってテーブルをビルドする
次の例は、プログラムで <xref:System.Windows.Documents.Table> を作成してデータを格納する方法を示しています。  テーブルの内容は、5 行 \(<xref:System.Windows.Documents.Table.RowGroups%2A> オブジェクトに含まれる <xref:System.Windows.Documents.TableRow> オブジェクトで指定\) と 6 列 \(<xref:System.Windows.Documents.TableColumn> オブジェクトで指定\) に配分されます。  行はさまざまな表示目的に使用されます。たとえば、タイトル行はテーブル全体のタイトルの設定に使用され、ヘッダー行はテーブル内のデータ列の説明、フッター行は要約情報の格納に使用されます。  "タイトル"、"ヘッダー"、および "フッター" 行の概念はテーブルに固有のものではなく、単純に異なる特性を持つ行です。  テーブルのセルには実際の内容が格納されます。テキスト、画像、またはその他のほとんどすべての [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 要素を格納できます。  
  
## 使用例  
 まず、<xref:System.Windows.Documents.Table> を格納する <xref:System.Windows.Documents.FlowDocument> を作成し、新しい <xref:System.Windows.Documents.Table> を作成して <xref:System.Windows.Documents.FlowDocument> に追加します。  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## 使用例  
 次に、6 つの <xref:System.Windows.Documents.TableColumn> オブジェクトを作成してテーブルの <xref:System.Windows.Documents.Table.Columns%2A> コレクションに追加し、書式を適用します。  
  
> [!NOTE]
>  テーブルの <xref:System.Windows.Documents.Table.Columns%2A> コレクションでは、標準のゼロから始まるインデックスを使用します。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## 使用例  
 次に、タイトル行を作成してテーブルに追加し、書式を適用します。  タイトル行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## 使用例  
 次に、ヘッダー行を作成してテーブルに追加し、ヘッダー行のセルを作成してデータを格納します。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## 使用例  
 次に、データ行を作成してテーブルに追加し、この行のセルを作成してデータを格納します。  この行の作成は、ヘッダー行の作成に似ていますが、適用する書式が少し異なります。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## 使用例  
 最後に、フッター行を作成して追加し、書式を設定します。  タイトル行と同様に、フッター行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## 参照  
 [テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)