---
title: TextElement コンテンツ モデルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: 4a50e8a10563fdc5e16ee2e2a46389e13b51e447
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548858"
---
# <a name="textelement-content-model-overview"></a>TextElement コンテンツ モデルの概要
このコンテンツ モデルの概要で説明するサポートされているコンテンツを<xref:System.Windows.Documents.TextElement>です。 <xref:System.Windows.Documents.Paragraph>クラスは、型の<xref:System.Windows.Documents.TextElement>します。 コンテンツ モデルは、他のオブジェクトや要素に含めることのできるオブジェクトや要素を記述します。 この概要から派生したオブジェクトに使用されるコンテンツ モデルの概要を示します<xref:System.Windows.Documents.TextElement>です。 詳細については、次を参照してください。[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)です。  
  
  
<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>コンテンツ モデルの図  
 派生したクラスの次の図に、コンテンツ モデルをまとめたもの<xref:System.Windows.Documents.TextElement>だけでなく他の方法ではない`TextElement`クラスのこのモデルに適合します。  
  
 ![図: フロー コンテンツ コンテインメント スキーマ] (../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 前の図からわかるように、許容される要素の子は必ずしもによって決定されませんからクラスを派生するかどうか、<xref:System.Windows.Documents.Block>クラスまたは<xref:System.Windows.Documents.Inline>クラスです。 たとえば、 <xref:System.Windows.Documents.Span> (、 <xref:System.Windows.Documents.Inline>-派生クラス) しか持てない<xref:System.Windows.Documents.Inline>子要素が、 <xref:System.Windows.Documents.Figure> (も、 <xref:System.Windows.Documents.Inline>-派生クラス) しか持てない<xref:System.Windows.Documents.Block>子要素です。 そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。 たとえば、みましょう図を使用して、フロー コンテンツを構築する方法を決定する<xref:System.Windows.Controls.RichTextBox>です。  
  
1.  A<xref:System.Windows.Controls.RichTextBox>含める必要があります、<xref:System.Windows.Documents.FlowDocument>をさらに含んでいる必要があります、 <xref:System.Windows.Documents.Block>-派生オブジェクト。 上の図に対応するセグメントを次に示します。  
  
     ![図: RichTextBox コンテインメント規則] (../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     この段階では、マークアップは次のようになります。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  に従って、ダイアグラムは、いくつか<xref:System.Windows.Documents.Block>などから選択する要素<xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.Section>、 <xref:System.Windows.Documents.Table>、 <xref:System.Windows.Documents.List>、および<xref:System.Windows.Documents.BlockUIContainer>(図でのブロックから派生したクラスを参照してください)。 たいと、<xref:System.Windows.Documents.Table>です。 前の図では、に従って、<xref:System.Windows.Documents.Table>が含まれています、<xref:System.Windows.Documents.TableRowGroup>を含む<xref:System.Windows.Documents.TableRow>要素で、含める<xref:System.Windows.Documents.TableCell>要素が含まれている、 <xref:System.Windows.Documents.Block>-派生オブジェクト。 次に、対応するセグメントの<xref:System.Windows.Documents.Table>上の図から取得します。  
  
     ![図: Table の親/子スキーマ] (../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     対応するマークアップは次のとおりです。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  ここでも、1 つまたは複数<xref:System.Windows.Documents.Block>下にある要素が必要になる、<xref:System.Windows.Documents.TableCell>です。 簡単にするために、セル内にいくつかのテキストを配置することにします。 これにを使用して、<xref:System.Windows.Documents.Paragraph>で、<xref:System.Windows.Documents.Run>要素。 対応することを示すダイアグラムからセグメントを次に示します、<xref:System.Windows.Documents.Paragraph>かかることができます、<xref:System.Windows.Documents.Inline>要素とする、 <xref:System.Windows.Documents.Run> (、<xref:System.Windows.Documents.Inline>要素) プレーン テキストのみを取得できます。  
  
     ![図: Paragraph の親/子スキーマ] (../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![図: Run の親/子スキーマ] (../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 例全体をマークアップで次に示します。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>TextElement のコンテンツをプログラムで操作する  
 内容、<xref:System.Windows.Documents.TextElement>コレクションの内容をプログラムで操作するため、作成されて<xref:System.Windows.Documents.TextElement>オブジェクトは、これらのコレクションで作業して行われます。 使用される 3 つの異なるコレクションがある<xref:System.Windows.Documents.TextElement>-派生クラス。  
  
-   <xref:System.Windows.Documents.InlineCollection>: のコレクションを表します<xref:System.Windows.Documents.Inline>要素。 <xref:System.Windows.Documents.InlineCollection> 許容される子コンテンツを定義、 <xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.Span>、および<xref:System.Windows.Controls.TextBlock>要素。  
  
-   <xref:System.Windows.Documents.BlockCollection>: のコレクションを表します<xref:System.Windows.Documents.Block>要素。 <xref:System.Windows.Documents.BlockCollection> は <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater>、<xref:System.Windows.Documents.Figure> 要素で許容される子コンテンツを定義します。  
  
-   <xref:System.Windows.Documents.ListItemCollection>: フロー コンテンツ要素を表す、順序付けられたで特定のコンテンツ項目または順序付けられていない<xref:System.Windows.Documents.List>です。  
  
 操作することができます (追加または項目を削除する) のそれぞれのプロパティを使用してこれらのコレクションから**インライン**、**ブロック**、および**Listitem**です。 次の例の Span を使用して、内容を操作する方法を示して、**インライン**プロパティです。  
  
> [!NOTE]
>  Table では、コンテンツの操作にいくつかのコレクションが使用されますが、これらのコレクションについてはここでは取り上げません。 詳細については、次を参照してください。[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)です。  
  
 次の例は、新しい作成<xref:System.Windows.Documents.Span>オブジェクト、および、使用、`Add`のコンテンツの子として 2 つのテキストを追加するメソッドの実行、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 次の例は、新しい作成<xref:System.Windows.Documents.Run>要素の先頭に挿入し、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 次の例の最後の削除<xref:System.Windows.Documents.Inline>内の要素、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、すべての内容を消去 (<xref:System.Windows.Documents.Inline>要素) から、<xref:System.Windows.Documents.Span>です。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>このコンテンツ モデルを共有する種類  
 次の型から継承、<xref:System.Windows.Documents.TextElement>クラスし、この概要で説明されているコンテンツを表示するために使用する可能性があります。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 この一覧にと共に配布非抽象型のみが含まれることに注意してください、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]です。 継承する他の種類を使用することがあります<xref:System.Windows.Documents.TextElement>です。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement オブジェクトを含むことのできる型  
 参照してください[WPF コンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Blocks プロパティを介してフロー コンテンツ要素を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)  
 [Blocks プロパティを介して FlowDocument を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Columns プロパティによってテーブルの列を操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [RowGroups プロパティを介してテーブルの行グループを操作する](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
