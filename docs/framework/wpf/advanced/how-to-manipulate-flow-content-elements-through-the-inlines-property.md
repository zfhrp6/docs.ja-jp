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
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a><span data-ttu-id="b2e43-102">方法 : Inlines プロパティを介してフロー コンテンツ要素を操作する</span><span class="sxs-lookup"><span data-stu-id="b2e43-102">How to: Manipulate Flow Content Elements through the Inlines Property</span></span>
<span data-ttu-id="b2e43-103">これらの例では、インライン フロー コンテンツ要素に対して実行できる一般的な操作の点を示しています (とそのような要素のコンテナーなど<xref:System.Windows.Controls.TextBlock>) を介して、**インライン**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b2e43-103">These examples demonstrate some of the more common operations that can be performed on inline flow content elements (and containers of such elements, such as <xref:System.Windows.Controls.TextBlock>) through the **Inlines** property.</span></span> <span data-ttu-id="b2e43-104">このプロパティを使用してアイテムの追加し、削除を<xref:System.Windows.Documents.InlineCollection>です。</span><span class="sxs-lookup"><span data-stu-id="b2e43-104">This property is used to add and remove items from <xref:System.Windows.Documents.InlineCollection>.</span></span> <span data-ttu-id="b2e43-105">フロー コンテンツ要素で、その機能、**インライン**プロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2e43-105">Flow content elements that feature an **Inlines** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 <span data-ttu-id="b2e43-106">使用する例<xref:System.Windows.Documents.Span>フローとして、コンテンツの要素が、これらの手法に適用可能なすべての要素またはコントロールをホストする、<xref:System.Windows.Documents.InlineCollection>コレクション。</span><span class="sxs-lookup"><span data-stu-id="b2e43-106">These examples happen to use <xref:System.Windows.Documents.Span> as the flow content element, but these techniques are applicable to all elements or controls that host an <xref:System.Windows.Documents.InlineCollection> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2e43-107">例</span><span class="sxs-lookup"><span data-stu-id="b2e43-107">Example</span></span>  
 <span data-ttu-id="b2e43-108">次の例は、新しい作成<xref:System.Windows.Documents.Span>オブジェクト、および、使用、**追加**のコンテンツの子として 2 つのテキストを追加するメソッドの実行、<xref:System.Windows.Documents.Span>です。</span><span class="sxs-lookup"><span data-stu-id="b2e43-108">The following example creates a new <xref:System.Windows.Documents.Span> object, and then uses the **Add** method to add two text runs as content children of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a><span data-ttu-id="b2e43-109">例</span><span class="sxs-lookup"><span data-stu-id="b2e43-109">Example</span></span>  
 <span data-ttu-id="b2e43-110">次の例は、新しい作成<xref:System.Windows.Documents.Run>要素の先頭に挿入し、<xref:System.Windows.Documents.Span>です。</span><span class="sxs-lookup"><span data-stu-id="b2e43-110">The following example creates a new <xref:System.Windows.Documents.Run> element and inserts it at the beginning of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a><span data-ttu-id="b2e43-111">例</span><span class="sxs-lookup"><span data-stu-id="b2e43-111">Example</span></span>  
 <span data-ttu-id="b2e43-112">次の例は、最上位レベルの数を取得<xref:System.Windows.Documents.Inline>に含まれる要素の<xref:System.Windows.Documents.Span>します。</span><span class="sxs-lookup"><span data-stu-id="b2e43-112">The following example gets the number of top-level <xref:System.Windows.Documents.Inline> elements contained in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a><span data-ttu-id="b2e43-113">例</span><span class="sxs-lookup"><span data-stu-id="b2e43-113">Example</span></span>  
 <span data-ttu-id="b2e43-114">次の例の最後の削除<xref:System.Windows.Documents.Inline>内の要素、<xref:System.Windows.Documents.Span>です。</span><span class="sxs-lookup"><span data-stu-id="b2e43-114">The following example deletes the last <xref:System.Windows.Documents.Inline> element in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a><span data-ttu-id="b2e43-115">例</span><span class="sxs-lookup"><span data-stu-id="b2e43-115">Example</span></span>  
 <span data-ttu-id="b2e43-116">次の例では、すべての内容を消去 (<xref:System.Windows.Documents.Inline>要素) から、<xref:System.Windows.Documents.Span>です。</span><span class="sxs-lookup"><span data-stu-id="b2e43-116">The following example clears all of the contents (<xref:System.Windows.Documents.Inline> elements) from the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a><span data-ttu-id="b2e43-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2e43-117">See Also</span></span>  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [<span data-ttu-id="b2e43-118">フロー ドキュメントの概要</span><span class="sxs-lookup"><span data-stu-id="b2e43-118">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="b2e43-119">Blocks プロパティを介して FlowDocument を操作する</span><span class="sxs-lookup"><span data-stu-id="b2e43-119">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="b2e43-120">Columns プロパティによってテーブルの列を操作する</span><span class="sxs-lookup"><span data-stu-id="b2e43-120">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [<span data-ttu-id="b2e43-121">RowGroups プロパティを介してテーブルの行グループを操作する</span><span class="sxs-lookup"><span data-stu-id="b2e43-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
