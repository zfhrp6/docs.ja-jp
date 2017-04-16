---
title: "TextElement コンテンツ モデルの概要 | Microsoft Docs"
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
  - "ドキュメント, フロー ドキュメント"
  - "フロー コンテンツ要素 [WPF], TextElement コンテンツ モデル"
  - "フロー ドキュメント"
  - "TextElement コンテンツ モデル"
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# TextElement コンテンツ モデルの概要
このコンテンツ モデルの概要では、<xref:System.Windows.Documents.TextElement> でサポートされるコンテンツについて説明します。  <xref:System.Windows.Documents.Paragraph> クラスは、<xref:System.Windows.Documents.TextElement> の一種です。  コンテンツ モデルは、他のオブジェクトや要素に含めることのできるオブジェクトや要素を記述します。  ここでは、<xref:System.Windows.Documents.TextElement> から派生したオブジェクトに対して使用するコンテンツ モデルの概要を示します。  詳細については、「[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)」を参照してください。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="text_element_classes"></a>   
## コンテンツ モデルの図  
 <xref:System.Windows.Documents.TextElement> から派生したクラスのコンテンツ モデルと、このモデルがその他の `TextElement` 以外のクラスにどのように適用されるかについてまとめたものを次の図に示します。  
  
 ![ダイアグラム: フロー コンテンツ コンテインメント スキーマ](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow\_Content\_Schema")  
  
 上の図からわかるように、要素で許容される子は、必ずしもクラスが <xref:System.Windows.Documents.Block> クラスと <xref:System.Windows.Documents.Inline> クラスのどちらから派生したかによって決まるわけではありません。  たとえば、<xref:System.Windows.Documents.Span> \(<xref:System.Windows.Documents.Inline> の派生クラス\) は <xref:System.Windows.Documents.Inline> 子要素だけを持つことができるのに対し、<xref:System.Windows.Documents.Figure> \(同じく <xref:System.Windows.Documents.Inline> の派生クラス\) は <xref:System.Windows.Documents.Block> 子要素だけを持つことができます。  そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。  例として、<xref:System.Windows.Controls.RichTextBox> のフロー コンテンツを構築する方法を、上の図を使用して判断してみましょう。  
  
1.  <xref:System.Windows.Controls.RichTextBox> は <xref:System.Windows.Documents.FlowDocument> を含んでいる必要があり、<xref:System.Windows.Documents.FlowDocument> は <xref:System.Windows.Documents.Block> の派生オブジェクトを含んでいる必要があります。  上の図に対応するセグメントを次に示します。  
  
     ![ダイアグラム: RichTextBox コンテインメント規則](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow\_Ovw\_SchemaWalkThrough1")  
  
     この段階では、マークアップは次のようになります。  
  
     [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  上の図によると、<xref:System.Windows.Documents.Block> 要素には、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.Table>、<xref:System.Windows.Documents.List>、および <xref:System.Windows.Documents.BlockUIContainer> を含む、いくつかの選択肢があります \(上の図の Block の派生クラスを参照\)。  ここで、<xref:System.Windows.Documents.Table> が必要だとします。  上の図によると、<xref:System.Windows.Documents.Table> は <xref:System.Windows.Documents.TableRowGroup> を含んでおり、これは <xref:System.Windows.Documents.TableRow> 要素を含んでいます。さらにこれは <xref:System.Windows.Documents.TableCell> 要素を含んでおり、これは <xref:System.Windows.Documents.Block> の派生オブジェクトを含んでいます。  上の図の <xref:System.Windows.Documents.Table> に対応する部分を次に示します。  
  
     ![ダイアグラム: テーブルの親&#47;子スキーマ](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow\_Ovw\_SchemaWalkThrough2")  
  
     対応するマークアップは次のとおりです。  
  
     [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  さらに、<xref:System.Windows.Documents.TableCell> の下にも、1 つ以上の <xref:System.Windows.Documents.Block> 要素が必要です。  簡単にするために、セル内にいくつかのテキストを配置することにします。  これを行うには、<xref:System.Windows.Documents.Paragraph> を <xref:System.Windows.Documents.Run> 要素と組み合わせて使用します。  上の図でこれに対応する部分を次に示します。ここには、<xref:System.Windows.Documents.Paragraph> が <xref:System.Windows.Documents.Inline> 要素を取ることができ、<xref:System.Windows.Documents.Run> \(<xref:System.Windows.Documents.Inline> 要素の 1 つ\) がプレーンテキストのみを取ることができることが示されています。  
  
     ![ダイアグラム: 段落の親&#47;子スキーマ](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow\_Ovw\_SchemaWalkThrough3")  
  
     ![ダイアグラム: 実行の親&#47;子スキーマ](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow\_Ovw\_SchemaWalkThrough4")  
  
 例全体をマークアップで次に示します。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## TextElement のコンテンツをプログラムで操作する  
 <xref:System.Windows.Documents.TextElement> のコンテンツはコレクションで構成されているため、<xref:System.Windows.Documents.TextElement> オブジェクトのコンテンツをプログラムで操作するには、これらのコレクションを操作すればよいことになります。  <xref:System.Windows.Documents.TextElement> の派生クラスで使用されるコレクションには、次の 3 種類があります。  
  
-   <xref:System.Windows.Documents.InlineCollection>: <xref:System.Windows.Documents.Inline> 要素のコレクションを表します。  <xref:System.Windows.Documents.InlineCollection> は、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Span>、および <xref:System.Windows.Controls.TextBlock> 要素で許容される子コンテンツを定義します。  
  
-   <xref:System.Windows.Documents.BlockCollection>: <xref:System.Windows.Documents.Block> 要素のコレクションを表します。  <xref:System.Windows.Documents.BlockCollection> は、<xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater>、および <xref:System.Windows.Documents.Figure> 要素で許容される子コンテンツを定義します。  
  
-   <xref:System.Windows.Documents.ListItemCollection> : 順序付きまたは順序の付いていない <xref:System.Windows.Documents.List> 内の特定のコンテンツ項目を表すフロー コンテンツ要素。  
  
 これらのコレクションを操作 \(項目を追加または削除\) するには、それぞれ **Inlines**、**Blocks**、および **ListItems** プロパティを使用します。  Span のコンテンツを **Inlines** プロパティを使用して操作する方法を次の例に示します。  
  
> [!NOTE]
>  Table では、コンテンツの操作にいくつかのコレクションが使用されますが、これらのコレクションについてはここでは取り上げません。  詳細については、「[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)」を参照してください。  
  
 次の例では、新しい <xref:System.Windows.Documents.Span> オブジェクトを作成した後、`Add` メソッドを使用して、2 つのテキスト ランを <xref:System.Windows.Documents.Span> のコンテンツの子として追加します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 次の例では、新しい <xref:System.Windows.Documents.Run> 要素を作成して <xref:System.Windows.Documents.Span> の先頭に挿入します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 次の例では、<xref:System.Windows.Documents.Span> 内の最後の <xref:System.Windows.Documents.Inline> 要素を削除します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、<xref:System.Windows.Documents.Span> からすべての内容 \(<xref:System.Windows.Documents.Inline> 要素\) を消去します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## このコンテンツ モデルを共有する型  
 次に示す型は、<xref:System.Windows.Documents.TextElement> クラスから継承され、この概要で説明したコンテンツを表示するために使用できます。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 この一覧には、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] と共に配布される非抽象型しか含まれていません。  <xref:System.Windows.Documents.TextElement> を継承するその他の種類も使用できます。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## TextElement オブジェクトを含むことのできる型  
 「[WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)」を参照してください。  
  
## 参照  
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Blocks プロパティを介してフロー コンテンツ要素を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)   
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Columns プロパティによってテーブルの列を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)