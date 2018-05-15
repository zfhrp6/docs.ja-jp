---
title: '方法 : 中抜きの文字列を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: c79f5c1c6812b1175119133664e39995af29bd4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="e5ad2-102">方法 : 中抜きの文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="e5ad2-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="e5ad2-103">ほとんどの場合、テキスト文字列内に装飾を追加するときに、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションでは、個別の文字、またはグリフのコレクションの観点からテキストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="e5ad2-104">たとえば、線形グラデーション ブラシを作成し、適用、<xref:System.Windows.Controls.Control.Foreground%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="e5ad2-105">表示またはテキスト ボックスを編集するときに、現在のテキスト文字列の文字のセットに線形グラデーション ブラシが自動的に適用します。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="e5ad2-106">![線形グラデーション ブラシで表示されるテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="e5ad2-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="e5ad2-107">テキスト ボックスに適用された線形グラデーション ブラシの例</span><span class="sxs-lookup"><span data-stu-id="e5ad2-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="e5ad2-108">ただし、変換することもにテキストを<xref:System.Windows.Media.Geometry>オブジェクト、その他の種類の視覚的に豊富なテキストを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="e5ad2-109">たとえば、作成した、<xref:System.Windows.Media.Geometry>テキスト文字列のアウトラインに基づいてオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="e5ad2-110">![線形グラデーション ブラシを使用するテキスト アウトライン](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="e5ad2-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="e5ad2-111">テキストのアウトライン ジオメトリに適用される線形グラデーション ブラシの例</span><span class="sxs-lookup"><span data-stu-id="e5ad2-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="e5ad2-112">テキストに変換するときに、<xref:System.Windows.Media.Geometry>オブジェクト、文字のコレクションではなくなりました: テキスト文字列内の文字を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="e5ad2-113">ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="e5ad2-114">ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="e5ad2-115">次の例では、変換されたテキストの塗りつぶし、ストロークを変更して視覚効果を作成するいくつかの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="e5ad2-116">![塗りつぶしとストロークを別の色を含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="e5ad2-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="e5ad2-117">ストロークと塗りつぶしを別々の色に設定した例</span><span class="sxs-lookup"><span data-stu-id="e5ad2-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="e5ad2-118">![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="e5ad2-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="e5ad2-119">ストロークに適用したイメージ ブラシの例</span><span class="sxs-lookup"><span data-stu-id="e5ad2-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="e5ad2-120">境界ボックスの四角形、または変換されたテキストの強調表示を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="e5ad2-121">次の例は、ストロークおよび変換されたテキストの強調表示を変更することによって、視覚効果を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="e5ad2-122">![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="e5ad2-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="e5ad2-123">ストロークと強調表示に適用したイメージ ブラシの例</span><span class="sxs-lookup"><span data-stu-id="e5ad2-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5ad2-124">例</span><span class="sxs-lookup"><span data-stu-id="e5ad2-124">Example</span></span>  
 <span data-ttu-id="e5ad2-125">テキストを変換するキー、<xref:System.Windows.Media.Geometry>オブジェクトは、使用する、<xref:System.Windows.Media.FormattedText>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="e5ad2-126">使用することがこのオブジェクトを作成した後、<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>と<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>をテキストに変換するメソッド<xref:System.Windows.Media.Geometry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="e5ad2-127">最初のメソッドは、フォーマットされたテキストのジオメトリを返します2 番目のメソッドは、境界ボックスの書式設定されたテキストのジオメトリを返します。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="e5ad2-128">次のコード例を作成する方法を示しています、<xref:System.Windows.Media.FormattedText>オブジェクトの書式設定されたテキストと、境界ボックスのジオメトリを取得するとします。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="e5ad2-129">取得した表示するために、<xref:System.Windows.Media.Geometry>オブジェクトにアクセスする必要があります、<xref:System.Windows.Media.DrawingContext>変換されたテキストが表示されているオブジェクトの。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="e5ad2-130">これらのコード例では、これはユーザー定義のレンダリングをサポートするクラスから派生したカスタム コントロール オブジェクトを作成することで行われます。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="e5ad2-131">表示する<xref:System.Windows.Media.Geometry>、カスタム コントロール内のオブジェクトのオーバーライドを提供する、<xref:System.Windows.UIElement.OnRender%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="e5ad2-132">オーバーライドされたメソッドを使用する必要があります、<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>を描画するメソッド、<xref:System.Windows.Media.Geometry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e5ad2-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a><span data-ttu-id="e5ad2-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5ad2-133">See Also</span></span>  
 [<span data-ttu-id="e5ad2-134">書式設定されたテキストの描画</span><span class="sxs-lookup"><span data-stu-id="e5ad2-134">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
