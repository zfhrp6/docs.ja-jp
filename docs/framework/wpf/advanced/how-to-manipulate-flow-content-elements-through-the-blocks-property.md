---
title: "方法 : Blocks プロパティを介してフロー コンテンツ要素を操作する | Microsoft Docs"
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
  - "Blocks プロパティ, 操作 (フロー コンテンツ要素を)"
  - "ドキュメント, 操作 (Blocks プロパティを介してフロー コンテンツ要素を)"
  - "フロー コンテンツ要素, 操作 (Blocks プロパティを介して)"
  - "プロパティ, ブロック, 操作 (フロー コンテンツ要素を)"
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : Blocks プロパティを介してフロー コンテンツ要素を操作する
ここでは、**Blocks** プロパティを使用してフロー コンテンツ要素に対して実行できるいくつかの一般的な操作を示します。  このプロパティは、<xref:System.Windows.Documents.BlockCollection> の項目を追加および削除するために使用します。  **Blocks** プロパティを備えたフロー コンテンツ要素には、以下のものがあります。  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 このトピックの例では、フロー コンテンツ要素として <xref:System.Windows.Documents.Section> を使用していますが、フロー コンテンツ要素コレクションをホストするすべての要素に同じ手法を適用できます。  
  
## 使用例  
 次の例では、新しい <xref:System.Windows.Documents.Section> を作成し、**Add** メソッドを使用して **Section** コンテンツに新しい Paragraph を追加します。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## 使用例  
 次の例では、新しい <xref:System.Windows.Documents.Paragraph> 要素を作成して <xref:System.Windows.Documents.Section> の先頭に挿入します。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Documents.Section> に含まれているトップレベルの <xref:System.Windows.Documents.Block> 要素の数を取得します。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Documents.Section> 内の最後の <xref:System.Windows.Documents.Block> 要素を削除します。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Documents.Section> からすべての内容 \(<xref:System.Windows.Documents.Block> 要素\) を消去します。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## 参照  
 <xref:System.Windows.Documents.BlockCollection>   
 <xref:System.Windows.Documents.InlineCollection>   
 <xref:System.Windows.Documents.ListItemCollection>   
 [フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)   
 [Columns プロパティによってテーブルの列を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)