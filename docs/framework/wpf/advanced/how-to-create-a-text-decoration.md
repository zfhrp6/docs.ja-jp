---
title: "方法 : 文字の装飾を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9229ce86dbe640c4eb960c455dd049ff40b38d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="160a6-102">方法 : 文字の装飾を作成する</span><span class="sxs-lookup"><span data-stu-id="160a6-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="160a6-103">A<xref:System.Windows.TextDecoration>オブジェクトがテキストに追加できるビジュアルの装飾します。</span><span class="sxs-lookup"><span data-stu-id="160a6-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="160a6-104">文字の装飾の 4 つの種類があります: 下線、基準、取り消し線、および上線。</span><span class="sxs-lookup"><span data-stu-id="160a6-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="160a6-105">次の例は、文字の装飾のテキストに対する相対位置を示します。</span><span class="sxs-lookup"><span data-stu-id="160a6-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="160a6-106">![テキスト装飾位置のダイアグラム](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="160a6-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="160a6-107">テキスト装飾の種類の例</span><span class="sxs-lookup"><span data-stu-id="160a6-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="160a6-108">テキストに文字の装飾を追加するには、作成、<xref:System.Windows.TextDecoration>オブジェクトし、そのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="160a6-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="160a6-109">使用して、<xref:System.Windows.TextDecoration.Location%2A>文字飾りが表示される場所、下線などの文字を指定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="160a6-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="160a6-110">使用して、<xref:System.Windows.TextDecoration.Pen%2A>文字飾りを純色の塗りつぶしのグラデーションの色などの外観を指定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="160a6-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="160a6-111">値を指定しない場合、<xref:System.Windows.TextDecoration.Pen%2A>プロパティ、テキストと同じ色に装飾の既定値です。</span><span class="sxs-lookup"><span data-stu-id="160a6-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="160a6-112">定義した後、<xref:System.Windows.TextDecoration>オブジェクトに追加して、<xref:System.Windows.TextDecorations>目的のテキスト オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="160a6-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="160a6-113">次の例では、線形グラデーション ブラシとペンの破線スタイルが設定されているテキスト装飾を示します。</span><span class="sxs-lookup"><span data-stu-id="160a6-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="160a6-114">![線形グラデーション下線付き文字飾り](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="160a6-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="160a6-115">線形グラデーションのスタイルの下線の例ブラシ、ペンの破線</span><span class="sxs-lookup"><span data-stu-id="160a6-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="160a6-116"><xref:System.Windows.Documents.Hyperlink>オブジェクトはインライン レベル フロー コンテンツ要素フロー コンテンツ内のハイパーリンクをホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="160a6-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="160a6-117">既定では、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.TextDecoration>下線を表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="160a6-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="160a6-118"><xref:System.Windows.TextDecoration>オブジェクトができる処理を要するインスタンスを作成すると、パフォーマンスが多数ある場合に特に<xref:System.Windows.Documents.Hyperlink>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="160a6-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="160a6-119">広範な利用を加えた場合<xref:System.Windows.Documents.Hyperlink>要素、するをお勧めしますように、イベントをトリガーする場合にのみ下線を表示、<xref:System.Windows.ContentElement.MouseEnter>イベント。</span><span class="sxs-lookup"><span data-stu-id="160a6-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="160a6-120">次の例では、"My MSN"リンクの下線は動的 — これ場合のみ表示されます、<xref:System.Windows.ContentElement.MouseEnter>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="160a6-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="160a6-121">![Textdecorations を表示するハイパーリンク](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="160a6-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="160a6-122">Textdecorations をで定義されているハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="160a6-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="160a6-123">詳細については、「[方法: ハイパーリンクに下線を引くかどうかを指定する](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="160a6-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="160a6-124">例</span><span class="sxs-lookup"><span data-stu-id="160a6-124">Example</span></span>  
 <span data-ttu-id="160a6-125">次のコード例では、下線の文字装飾は、フォントの既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="160a6-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="160a6-126">次のコード例では、下線の文字装飾を純色のブラシ、ペンを使用した作成されます。</span><span class="sxs-lookup"><span data-stu-id="160a6-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="160a6-127">次のコード例では、下線の文字装飾を破線のペンの線形グラデーション ブラシを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="160a6-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="160a6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="160a6-128">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="160a6-129">ハイパーリンクに下線を引くかどうかを指定する</span><span class="sxs-lookup"><span data-stu-id="160a6-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
