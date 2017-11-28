---
title: "方法 : TileBrush の水平方向および垂直方向の配置を設定する"
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
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c581bb167c020e9e4f0de26b0e17e7a1d70704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a><span data-ttu-id="9c8c7-102">方法 : TileBrush の水平方向および垂直方向の配置を設定する</span><span class="sxs-lookup"><span data-stu-id="9c8c7-102">How to: Set the Horizontal and Vertical Alignment of a TileBrush</span></span>
<span data-ttu-id="9c8c7-103">この例は、タイル内の内容の水平方向および垂直の配置を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-103">This example shows how to control the horizontal and vertical alignment of content in a tile.</span></span> <span data-ttu-id="9c8c7-104">水平方向および垂直方向の配置を制御する、<xref:System.Windows.Media.TileBrush>を使用してその<xref:System.Windows.Media.TileBrush.AlignmentX%2A>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-104">To control the horizontal and vertical alignment of a <xref:System.Windows.Media.TileBrush>, use its <xref:System.Windows.Media.TileBrush.AlignmentX%2A> and <xref:System.Windows.Media.TileBrush.AlignmentY%2A> properties.</span></span>  
  
 <span data-ttu-id="9c8c7-105"><xref:System.Windows.Media.TileBrush.AlignmentX%2A>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>のプロパティ、<xref:System.Windows.Media.TileBrush>使用は、次の条件のいずれかが true の場合。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-105">The <xref:System.Windows.Media.TileBrush.AlignmentX%2A> and <xref:System.Windows.Media.TileBrush.AlignmentY%2A> properties of a <xref:System.Windows.Media.TileBrush> are used when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="9c8c7-106"><xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティは<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>と<xref:System.Windows.Media.TileBrush.Viewbox%2A>と<xref:System.Windows.Media.TileBrush.Viewport%2A>別の縦横比があります。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-106">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property is <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill> and the <xref:System.Windows.Media.TileBrush.Viewbox%2A> and <xref:System.Windows.Media.TileBrush.Viewport%2A> have different aspect ratios.</span></span>  
  
-   <span data-ttu-id="9c8c7-107"><xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティは<xref:System.Windows.Media.Stretch.None>と<xref:System.Windows.Media.TileBrush.Viewbox%2A>と<xref:System.Windows.Media.TileBrush.Viewport%2A>サイズが異なる。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-107">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property is <xref:System.Windows.Media.Stretch.None> and the <xref:System.Windows.Media.TileBrush.Viewbox%2A> and <xref:System.Windows.Media.TileBrush.Viewport%2A> are different sizes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c8c7-108">例</span><span class="sxs-lookup"><span data-stu-id="9c8c7-108">Example</span></span>  
 <span data-ttu-id="9c8c7-109">次の例の内容、<xref:System.Windows.Media.DrawingBrush>の型である<xref:System.Windows.Media.TileBrush>、そのタイルの左上隅にします。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-109">The following example aligns the content of a <xref:System.Windows.Media.DrawingBrush>, which is a type of <xref:System.Windows.Media.TileBrush>, to the upper-left corner of its tile.</span></span> <span data-ttu-id="9c8c7-110">例のセット、コンテンツに合わせて、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>のプロパティ、<xref:System.Windows.Media.DrawingBrush>に<xref:System.Windows.Media.AlignmentX.Left>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>プロパティを<xref:System.Windows.Media.AlignmentY.Top>です。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-110">To align the content, the example sets the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property of the <xref:System.Windows.Media.DrawingBrush> to <xref:System.Windows.Media.AlignmentX.Left> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Top>.</span></span> <span data-ttu-id="9c8c7-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-111">This example produces the following output.</span></span>  
  
 <span data-ttu-id="9c8c7-112">![上部 &#45;された TileBrush; 左揃え](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")</span><span class="sxs-lookup"><span data-stu-id="9c8c7-112">![A TileBrush with top&#45;left alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")</span></span>  
<span data-ttu-id="9c8c7-113">内容が左上隅に配置された TileBrush</span><span class="sxs-lookup"><span data-stu-id="9c8c7-113">TileBrush with content aligned to the upper-left corner</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a><span data-ttu-id="9c8c7-114">例</span><span class="sxs-lookup"><span data-stu-id="9c8c7-114">Example</span></span>  
 <span data-ttu-id="9c8c7-115">次の例の内容、<xref:System.Windows.Media.DrawingBrush>を設定して、タイルの右下隅に、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>プロパティを<xref:System.Windows.Media.AlignmentX.Right>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>プロパティを<xref:System.Windows.Media.AlignmentY.Bottom>です。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-115">The next example aligns the content of a <xref:System.Windows.Media.DrawingBrush> to the lower-right corner of its tile by setting the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property to <xref:System.Windows.Media.AlignmentX.Right> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Bottom>.</span></span> <span data-ttu-id="9c8c7-116">この例では次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-116">The example produces the following output.</span></span>  
  
 <span data-ttu-id="9c8c7-117">![下部にある &#45;された TileBrush; 右揃え](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")</span><span class="sxs-lookup"><span data-stu-id="9c8c7-117">![A TileBrush with bottom&#45;right alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")</span></span>  
<span data-ttu-id="9c8c7-118">内容が右下隅に配置された TileBrush</span><span class="sxs-lookup"><span data-stu-id="9c8c7-118">TileBrush with content aligned to the lower-right corner</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a><span data-ttu-id="9c8c7-119">例</span><span class="sxs-lookup"><span data-stu-id="9c8c7-119">Example</span></span>  
 <span data-ttu-id="9c8c7-120">次の例の内容、<xref:System.Windows.Media.DrawingBrush>を設定して、タイルの左上隅に、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>プロパティを<xref:System.Windows.Media.AlignmentX.Left>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>プロパティを<xref:System.Windows.Media.AlignmentY.Top>です。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-120">The next example aligns the content of a <xref:System.Windows.Media.DrawingBrush> to the upper-left corner of its tile by setting the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property to <xref:System.Windows.Media.AlignmentX.Left> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Top>.</span></span> <span data-ttu-id="9c8c7-121">また、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.TileMode%2A>の<xref:System.Windows.Media.DrawingBrush>タイル パターンを生成するためにします。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-121">It also sets the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> of the <xref:System.Windows.Media.DrawingBrush> to produce a tile pattern.</span></span> <span data-ttu-id="9c8c7-122">この例では次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-122">The example produces the following output.</span></span>  
  
 <span data-ttu-id="9c8c7-123">![上部 &#45;が並べて表示された TileBrush; 左揃え](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")</span><span class="sxs-lookup"><span data-stu-id="9c8c7-123">![A tiled TileBrush with top&#45;left alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")</span></span>  
<span data-ttu-id="9c8c7-124">基本タイルの左上に内容が配置されたタイル パターン</span><span class="sxs-lookup"><span data-stu-id="9c8c7-124">Tile pattern with content aligned to upper-left in base tile</span></span>  
  
 <span data-ttu-id="9c8c7-125">図では、内容がどのように配置されているかをわかりやすくするために、基本タイルが強調されています。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-125">The illustration highlights abase tile so that you can see how its content is aligned.</span></span> <span data-ttu-id="9c8c7-126">注意して、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>設定には効果がないため、コンテンツの<xref:System.Windows.Media.DrawingBrush>基本タイルが水平方向に完全にいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-126">Notice that the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> setting has no effect because the content of the <xref:System.Windows.Media.DrawingBrush> completely fills the base tile horizontally.</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a><span data-ttu-id="9c8c7-127">例</span><span class="sxs-lookup"><span data-stu-id="9c8c7-127">Example</span></span>  
 <span data-ttu-id="9c8c7-128">最後の例は、タイルのコンテンツを揃えます<xref:System.Windows.Media.DrawingBrush>を設定して基本タイルの右下に、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>プロパティを<xref:System.Windows.Media.AlignmentX.Right>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>プロパティを<xref:System.Windows.Media.AlignmentY.Bottom>です。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-128">The final example aligns the content of a tiled <xref:System.Windows.Media.DrawingBrush> to the lower-right of its base tile by setting the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property to <xref:System.Windows.Media.AlignmentX.Right> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Bottom>.</span></span> <span data-ttu-id="9c8c7-129">この例では次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-129">The example produces the following output.</span></span>  
  
 <span data-ttu-id="9c8c7-130">![A の下部にある &#45;TileBrush を並べて表示以外の場合は右揃え](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")</span><span class="sxs-lookup"><span data-stu-id="9c8c7-130">![A tiled TileBrush with bottom&#45;right alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")</span></span>  
<span data-ttu-id="9c8c7-131">基本タイルの右上に内容が配置されたタイル パターン</span><span class="sxs-lookup"><span data-stu-id="9c8c7-131">Tile pattern with content aligned to lower-right in base tile</span></span>  
  
 <span data-ttu-id="9c8c7-132">もう一度、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>設定には効果がないため、コンテンツの<xref:System.Windows.Media.DrawingBrush>基本タイルが水平方向に完全にいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-132">Again, the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> setting has no effect because the content of the <xref:System.Windows.Media.DrawingBrush> completely fills the base tile horizontally.</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 <span data-ttu-id="9c8c7-133">例を使用して<xref:System.Windows.Media.DrawingBrush>を示すためにオブジェクト方法、<xref:System.Windows.Media.TileBrush.AlignmentX%2A>と<xref:System.Windows.Media.TileBrush.AlignmentY%2A>プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-133">The examples use <xref:System.Windows.Media.DrawingBrush> objects to demonstrate how the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> and <xref:System.Windows.Media.TileBrush.AlignmentY%2A> properties are used.</span></span> <span data-ttu-id="9c8c7-134">これらのプロパティがすべてのタイル ブラシの動作は同じです: <xref:System.Windows.Media.DrawingBrush>、 <xref:System.Windows.Media.ImageBrush>、および<xref:System.Windows.Media.VisualBrush>です。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-134">These properties behave identically for all the tile brushes: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="9c8c7-135">タイル ブラシの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c8c7-135">For more information about tile brushes, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8c7-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c8c7-136">See Also</span></span>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="9c8c7-137">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="9c8c7-137">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
