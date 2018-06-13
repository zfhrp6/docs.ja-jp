---
title: '方法 : Inlines プロパティを介してフロー コンテンツ要素を操作する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: 3bbeac2eda8811939be3c710a8ce28349e7f0759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545572"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a>方法 : Inlines プロパティを介してフロー コンテンツ要素を操作する
これらの例では、インライン フロー コンテンツ要素に対して実行できる一般的な操作の点を示しています (とそのような要素のコンテナーなど<xref:System.Windows.Controls.TextBlock>) を介して、**インライン**プロパティです。 このプロパティを使用してアイテムの追加し、削除を<xref:System.Windows.Documents.InlineCollection>です。 フロー コンテンツ要素で、その機能、**インライン**プロパティが含まれます。  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 使用する例<xref:System.Windows.Documents.Span>フローとして、コンテンツの要素が、これらの手法に適用可能なすべての要素またはコントロールをホストする、<xref:System.Windows.Documents.InlineCollection>コレクション。  
  
## <a name="example"></a>例  
 次の例は、新しい作成<xref:System.Windows.Documents.Span>オブジェクト、および、使用、**追加**のコンテンツの子として 2 つのテキストを追加するメソッドの実行、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a>例  
 次の例は、新しい作成<xref:System.Windows.Documents.Run>要素の先頭に挿入し、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a>例  
 次の例は、最上位レベルの数を取得<xref:System.Windows.Documents.Inline>に含まれる要素の<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a>例  
 次の例の最後の削除<xref:System.Windows.Documents.Inline>内の要素、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a>例  
 次の例では、すべての内容を消去 (<xref:System.Windows.Documents.Inline>要素) から、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Columns プロパティによってテーブルの列を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
