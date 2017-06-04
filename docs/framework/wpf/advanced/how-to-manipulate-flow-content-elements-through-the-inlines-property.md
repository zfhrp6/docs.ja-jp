---
title: "方法 : Inlines プロパティを介してフロー コンテンツ要素を操作する | Microsoft Docs"
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
  - "ドキュメント, 操作 (Inlines プロパティを介してフロー コンテンツ要素を)"
  - "フロー コンテンツ要素, 操作 (Inlines プロパティを介して)"
  - "Inlines プロパティ, 操作 (フロー コンテンツ要素を)"
  - "プロパティ, Inlines, 操作 (フロー コンテンツ要素を)"
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Inlines プロパティを介してフロー コンテンツ要素を操作する
以下の例では、**Inlines** プロパティを使用してインライン フロー コンテンツ要素 \(およびこのような要素の <xref:System.Windows.Controls.TextBlock> などのコンテナー\) に対して実行できるいくつかの一般的な操作を示します。  このプロパティは、<xref:System.Windows.Documents.InlineCollection> の項目を追加および削除するために使用します。  **Inlines** プロパティを備えたフロー コンテンツ要素には、以下のものがあります。  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 このトピックの例では、フロー コンテンツ要素として <xref:System.Windows.Documents.Span> を使用していますが、<xref:System.Windows.Documents.InlineCollection> コレクションをホストするすべての要素またはコントロールに同じ手法を適用できます。  
  
## 使用例  
 次の例では、新しい <xref:System.Windows.Documents.Span> オブジェクトを作成した後、**Add** メソッドを使用して、2 つのテキスト ランを <xref:System.Windows.Documents.Span> のコンテンツの子として追加します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## 使用例  
 次の例では、新しい <xref:System.Windows.Documents.Run> 要素を作成して <xref:System.Windows.Documents.Span> の先頭に挿入します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Documents.Span> に含まれているトップレベルの <xref:System.Windows.Documents.Inline> 要素の数を取得します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Documents.Span> 内の最後の <xref:System.Windows.Documents.Inline> 要素を削除します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Documents.Span> からすべての内容 \(<xref:System.Windows.Documents.Inline> 要素\) を消去します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## 参照  
 <xref:System.Windows.Documents.BlockCollection>   
 <xref:System.Windows.Documents.InlineCollection>   
 <xref:System.Windows.Documents.ListItemCollection>   
 [フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Columns プロパティによってテーブルの列を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)