---
title: "TileBrush の概要"
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
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d5e9fa36ddeda0c724eeb0bb46a64d0ba36c99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="tilebrush-overview"></a><span data-ttu-id="25f2b-102">TileBrush の概要</span><span class="sxs-lookup"><span data-stu-id="25f2b-102">TileBrush Overview</span></span>
<span data-ttu-id="25f2b-103"><xref:System.Windows.Media.TileBrush>オブジェクトを使用する、イメージで領域を描画する方法を細かく制御が大幅に向上<xref:System.Windows.Media.Drawing>、または<xref:System.Windows.Media.Visual>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-103"><xref:System.Windows.Media.TileBrush> objects provide you with a great deal of control over how an area is painted with an image, <xref:System.Windows.Media.Drawing>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="25f2b-104">このトピックを使用する方法について説明<xref:System.Windows.Media.TileBrush>の機能をより細かく方法、 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>領域を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="25f2b-104">This topic describes how to use <xref:System.Windows.Media.TileBrush> features to gain more control over how an <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, or <xref:System.Windows.Media.VisualBrush> paints an area.</span></span>  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a><span data-ttu-id="25f2b-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="25f2b-105">Prerequisites</span></span>  
 <span data-ttu-id="25f2b-106">このトピックの内容を理解するのにはの基本的な機能を使用する方法を理解しておいて、 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="25f2b-106">To understand this topic, it's helpful to understand how to use the basic features of the <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, or <xref:System.Windows.Media.VisualBrush> class.</span></span> <span data-ttu-id="25f2b-107">これらの型の概要については、次を参照してください。、[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-107">For an introduction to these types, see the [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a><span data-ttu-id="25f2b-108">タイルで領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="25f2b-108">Painting an Area with Tiles</span></span>  
 <span data-ttu-id="25f2b-109"><xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、は<xref:System.Windows.Media.VisualBrush>種類<xref:System.Windows.Media.TileBrush>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="25f2b-109"><xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, are <xref:System.Windows.Media.VisualBrush> are types of <xref:System.Windows.Media.TileBrush> objects.</span></span> <span data-ttu-id="25f2b-110">タイル ブラシを使用すると、イメージ、描画、またはビジュアルで領域を塗りつぶす方法を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-110">Tile brushes provide you with a great deal of control over how an area is painted with an image, drawing, or visual.</span></span> <span data-ttu-id="25f2b-111">たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-111">For example, instead of just painting an area with a single stretched image, you can paint an area with a series of image tiles that create a pattern.</span></span>  
  
 <span data-ttu-id="25f2b-112">タイル ブラシによる領域の塗りつぶしには、コンテンツ、基本タイル、および出力領域の 3 つのコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-112">Painting an area with a tile brush involves three components: content, the base tile, and the output area.</span></span>  
  
 <span data-ttu-id="25f2b-113">![TileBrush コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")</span><span class="sxs-lookup"><span data-stu-id="25f2b-113">![TileBrush components](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")</span></span>  
<span data-ttu-id="25f2b-114">1 つのタイルが TileBrush のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="25f2b-114">Components of a TileBrush with a single tile</span></span>  
  
 <span data-ttu-id="25f2b-115">![並べて表示された TileBrush のコンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")</span><span class="sxs-lookup"><span data-stu-id="25f2b-115">![Components of a tiled TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")</span></span>  
<span data-ttu-id="25f2b-116">Tile の TileMode を使用する TileBrush のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="25f2b-116">Components of a TileBrush with a TileMode of Tile</span></span>  
  
 <span data-ttu-id="25f2b-117">出力領域のように、描画する領域が、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>または<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-117">The output area is the area being painted, such as the <xref:System.Windows.Shapes.Shape.Fill%2A> of an <xref:System.Windows.Shapes.Ellipse> or the <xref:System.Windows.Controls.Control.Background%2A> of a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="25f2b-118">次のセクションでは、の他の 2 つのコンポーネントを記述する、<xref:System.Windows.Media.TileBrush>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-118">The next sections describe the other two components of a <xref:System.Windows.Media.TileBrush>.</span></span>  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a><span data-ttu-id="25f2b-119">ブラシのコンテンツ</span><span class="sxs-lookup"><span data-stu-id="25f2b-119">Brush Content</span></span>  
 <span data-ttu-id="25f2b-120">3 つの種類がある<xref:System.Windows.Media.TileBrush>様々 な種類のコンテンツを描画各とします。</span><span class="sxs-lookup"><span data-stu-id="25f2b-120">There are three different types of <xref:System.Windows.Media.TileBrush> and each paints with a different type of content.</span></span>  
  
-   <span data-ttu-id="25f2b-121">ブラシがの場合、 <xref:System.Windows.Media.ImageBrush>、このコンテンツは、イメージ、<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティの内容を指定する、<xref:System.Windows.Media.ImageBrush>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-121">If the brush is an <xref:System.Windows.Media.ImageBrush>, this content is an image The <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property specifies the contents of the <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
-   <span data-ttu-id="25f2b-122">ブラシがの場合、 <xref:System.Windows.Media.DrawingBrush>、このコンテンツは、描画します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-122">If the brush is a <xref:System.Windows.Media.DrawingBrush>, this content is a drawing.</span></span> <span data-ttu-id="25f2b-123"><xref:System.Windows.Media.DrawingBrush.Drawing%2A>プロパティの内容を指定する、<xref:System.Windows.Media.DrawingBrush>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-123">The <xref:System.Windows.Media.DrawingBrush.Drawing%2A> property specifies the contents of the <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
-   <span data-ttu-id="25f2b-124">ブラシがの場合、 <xref:System.Windows.Media.VisualBrush>、このコンテンツは、ビジュアル。</span><span class="sxs-lookup"><span data-stu-id="25f2b-124">If the brush is a <xref:System.Windows.Media.VisualBrush>, this content is a visual.</span></span> <span data-ttu-id="25f2b-125"><xref:System.Windows.Media.VisualBrush.Visual%2A>プロパティの内容を指定する、<xref:System.Windows.Media.VisualBrush>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-125">The <xref:System.Windows.Media.VisualBrush.Visual%2A> property specifies the content of the <xref:System.Windows.Media.VisualBrush>.</span></span>  
  
 <span data-ttu-id="25f2b-126">位置および寸法を指定することができます<xref:System.Windows.Media.TileBrush>コンテンツを使用して、<xref:System.Windows.Media.TileBrush.Viewbox%2A>プロパティのままにするが一般的ですが、<xref:System.Windows.Media.TileBrush.Viewbox%2A>その既定値に設定します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-126">You can specify the position and dimensions of <xref:System.Windows.Media.TileBrush> content by using the <xref:System.Windows.Media.TileBrush.Viewbox%2A> property, although it is common to leave the <xref:System.Windows.Media.TileBrush.Viewbox%2A> set to its default value.</span></span> <span data-ttu-id="25f2b-127">既定では、<xref:System.Windows.Media.TileBrush.Viewbox%2A>ブラシの内容を完全に格納するように構成します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-127">By default, the <xref:System.Windows.Media.TileBrush.Viewbox%2A> is configured to completely contain the brush's contents.</span></span> <span data-ttu-id="25f2b-128">構成の詳細については、<xref:System.Windows.Controls.Viewbox>を参照してください、<xref:System.Windows.Controls.Viewbox>プロパティ ページ。</span><span class="sxs-lookup"><span data-stu-id="25f2b-128">For more information about configuring the <xref:System.Windows.Controls.Viewbox>, see the <xref:System.Windows.Controls.Viewbox> property page.</span></span>  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a><span data-ttu-id="25f2b-129">基本タイル</span><span class="sxs-lookup"><span data-stu-id="25f2b-129">The Base Tile</span></span>  
 <span data-ttu-id="25f2b-130">A<xref:System.Windows.Media.TileBrush>基本タイルの内容を射影します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-130">A <xref:System.Windows.Media.TileBrush> projects its content onto a base tile.</span></span> <span data-ttu-id="25f2b-131"><xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティ コントロール方法<xref:System.Windows.Media.TileBrush>コンテンツが基本タイルに合わせて引き伸ばされます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-131">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property controls how <xref:System.Windows.Media.TileBrush> content is stretched to fill the base tile.</span></span> <span data-ttu-id="25f2b-132"><xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.Stretch>列挙します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-132">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property accepts the following values, defined by the <xref:System.Windows.Media.Stretch> enumeration:</span></span>  
  
-   <span data-ttu-id="25f2b-133"><xref:System.Windows.Media.Stretch.None>: ブラシのコンテンツは、タイルに合わせて引き伸ばされますされません。</span><span class="sxs-lookup"><span data-stu-id="25f2b-133"><xref:System.Windows.Media.Stretch.None>: The brush's content is not stretched to fill the tile.</span></span>  
  
-   <span data-ttu-id="25f2b-134"><xref:System.Windows.Media.Stretch.Fill>: ブラシのコンテンツは、タイルに合わせてスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-134"><xref:System.Windows.Media.Stretch.Fill>: The brush's content is scaled to fit the tile.</span></span> <span data-ttu-id="25f2b-135">コンテンツの高さと幅は別々にスケーリングされるため、コンテンツの元の縦横比が維持されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="25f2b-135">Because the content's height and width are scaled independently, the original aspect ratio of the content might not be preserved.</span></span> <span data-ttu-id="25f2b-136">つまり、出力タイルを完全に塗りつぶすために、ブラシのコンテンツがいびつになることがあります。</span><span class="sxs-lookup"><span data-stu-id="25f2b-136">That is, the brush's content might be warped in order to completely fill the output tile.</span></span>  
  
-   <span data-ttu-id="25f2b-137"><xref:System.Windows.Media.Stretch.Uniform>: ブラシのコンテンツは、に、タイル内で完全に収まるようにスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-137"><xref:System.Windows.Media.Stretch.Uniform>: The brush's content is scaled so that it fits completely within the tile.</span></span> <span data-ttu-id="25f2b-138">コンテンツの縦横比は維持されます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-138">The content's aspect ratio is preserved.</span></span>  
  
-   <span data-ttu-id="25f2b-139"><xref:System.Windows.Media.Stretch.UniformToFill>: ブラシのコンテンツは、コンテンツの元の縦横比を維持しながら、出力領域が完全にいっぱいされるようにスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-139"><xref:System.Windows.Media.Stretch.UniformToFill>: The brush's content is scaled so that it completely fills the output area while preserving the content's original aspect ratio.</span></span>  
  
 <span data-ttu-id="25f2b-140">次の図は、さまざまな示します<xref:System.Windows.Media.TileBrush.Stretch%2A>設定します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-140">The following image illustrates the different <xref:System.Windows.Media.TileBrush.Stretch%2A> settings.</span></span>  
  
 <span data-ttu-id="25f2b-141">![TileBrush のさまざまな Stretch 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")</span><span class="sxs-lookup"><span data-stu-id="25f2b-141">![Different TileBrush Stretch settings](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")</span></span>  
  
 <span data-ttu-id="25f2b-142">次の例の内容、<xref:System.Windows.Media.ImageBrush>設定されているため、出力領域に合わせて伸縮しません。</span><span class="sxs-lookup"><span data-stu-id="25f2b-142">In the following example, the content of an <xref:System.Windows.Media.ImageBrush> is set so that it does not stretch to fill the output area.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 <span data-ttu-id="25f2b-143">既定では、 <xref:System.Windows.Media.TileBrush> 1 つのタイル (基本タイル) を生成し、出力領域がいっぱいにするには、そのタイルを拡大します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-143">By default, a <xref:System.Windows.Media.TileBrush> generates a single tile (the base tile) and stretches that tile to completely fill the output area.</span></span> <span data-ttu-id="25f2b-144">基本タイルの位置とサイズを変更するには設定して、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="25f2b-144">You can change the size and position of the base tile by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a><span data-ttu-id="25f2b-145">基本タイルのサイズ</span><span class="sxs-lookup"><span data-stu-id="25f2b-145">Base Tile Size</span></span>  
 <span data-ttu-id="25f2b-146"><xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティは、基本のタイルの位置とサイズを決定し、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを決定するかどうか、<xref:System.Windows.Media.TileBrush.Viewport%2A>絶対または相対座標を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-146">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property determines the size and position of the base tile, and the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property determines whether the <xref:System.Windows.Media.TileBrush.Viewport%2A> is specified using absolute or relative coordinates.</span></span> <span data-ttu-id="25f2b-147">座標が相対的な場合、座標は出力領域のサイズに対して相対的になります。</span><span class="sxs-lookup"><span data-stu-id="25f2b-147">If the coordinates are relative, they are relative to the size of the output area.</span></span> <span data-ttu-id="25f2b-148">点 (0,0) は出力領域の左上隅を表し、(1,1) は出力領域の右下隅を表します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-148">The point (0,0) represents the top left corner of the output area, and (1,1) represents the bottom right corner of the output area.</span></span> <span data-ttu-id="25f2b-149">指定する、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティが絶対座標を使用して、設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-149">To specify that the <xref:System.Windows.Media.TileBrush.Viewport%2A> property uses absolute coordinates, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
 <span data-ttu-id="25f2b-150">次の図に、出力の間の違い、<xref:System.Windows.Media.TileBrush>絶対と相対で<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-150">The following illustration shows the difference in output between a <xref:System.Windows.Media.TileBrush> with relative versus absolute <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>.</span></span> <span data-ttu-id="25f2b-151">どの図も、並べて表示するパターンを示しています。次のセクションでは、パターンの指定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-151">Notice that the illustrations each show a tiled pattern; the next section describes how to specify tile pattern.</span></span>  
  
 <span data-ttu-id="25f2b-152">![ビューポートの絶対単位と総体単位](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")</span><span class="sxs-lookup"><span data-stu-id="25f2b-152">![Absolute and Relative Viewport Units](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")</span></span>  
  
 <span data-ttu-id="25f2b-153">次の例では、イメージを使用して幅と高さが 50% のタイルを作成しています。</span><span class="sxs-lookup"><span data-stu-id="25f2b-153">In the following example, an image is used to create a tile that has a width and height of 50%.</span></span> <span data-ttu-id="25f2b-154">基本タイルは、出力領域の (0,0) の位置にあります。</span><span class="sxs-lookup"><span data-stu-id="25f2b-154">The base tile is located at (0,0) of the output area.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 <span data-ttu-id="25f2b-155">次の例では、のタイル、 <xref:System.Windows.Media.ImageBrush> 25 で 25 デバイス非依存のピクセルにします。</span><span class="sxs-lookup"><span data-stu-id="25f2b-155">The next example sets the tiles of an <xref:System.Windows.Media.ImageBrush> to 25 by 25 device independent pixels.</span></span> <span data-ttu-id="25f2b-156"><xref:System.Windows.Media.TileBrush.ViewportUnits%2A>絶対では、<xref:System.Windows.Media.ImageBrush>タイルは 25 で 25 (ピクセル単位) 描画される領域のサイズに関係なく、常にします。</span><span class="sxs-lookup"><span data-stu-id="25f2b-156">Because the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> are absolute, the <xref:System.Windows.Media.ImageBrush> tiles are always 25 by 25 pixels, regardless of the size of the area being painted.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a><span data-ttu-id="25f2b-157">並べて表示する動作</span><span class="sxs-lookup"><span data-stu-id="25f2b-157">Tiling Behavior</span></span>  
 <span data-ttu-id="25f2b-158">A<xref:System.Windows.Media.TileBrush>基本タイルが完全にいっぱいにならない、出力領域とし、他のタイル モード時に、並べて表示するパターンを生成する<xref:System.Windows.Media.TileMode.None>を指定します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-158">A <xref:System.Windows.Media.TileBrush> produces a tiled pattern when its base tile does not completely fill the output area and a tiling mode other then <xref:System.Windows.Media.TileMode.None> is specified.</span></span> <span data-ttu-id="25f2b-159">タイル ブラシのタイルが完全にいっぱいにならない、出力領域とその<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティ基本タイルが出力領域を塗りつぶすに複製する必要があり場合は、基本のタイル複製するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-159">When a tile brush's tile does not completely fill the output area, its <xref:System.Windows.Media.TileBrush.TileMode%2A> property specifies whether the base tile should be duplicated to fill the output area and, if so, how the base tile should be duplicated.</span></span> <span data-ttu-id="25f2b-160"><xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.TileMode>列挙します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-160">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property accepts the following values, defined by the <xref:System.Windows.Media.TileMode> enumeration:</span></span>  
  
-   <span data-ttu-id="25f2b-161"><xref:System.Windows.Media.TileMode.None>: 基本タイルのみが描画されます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-161"><xref:System.Windows.Media.TileMode.None>: Only the base tile is drawn.</span></span>  
  
-   <span data-ttu-id="25f2b-162"><xref:System.Windows.Media.TileMode.Tile>: 基本タイルが描画され、残りの領域が繰り返しで塗りつぶされます基本タイルを 1 つのタイルの右エッジは、次の左の端に同様に上下の。</span><span class="sxs-lookup"><span data-stu-id="25f2b-162"><xref:System.Windows.Media.TileMode.Tile>: The base tile is drawn and the remaining area is filled by repeating the base tile such that the right edge of one tile is adjacent to the left edge of the next, and similarly for bottom and top.</span></span>  
  
-   <span data-ttu-id="25f2b-163"><xref:System.Windows.Media.TileMode.FlipX>: 同じ<xref:System.Windows.Media.TileMode.Tile>、が、タイルの代替列が水平方向に反転します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-163"><xref:System.Windows.Media.TileMode.FlipX>: The same as <xref:System.Windows.Media.TileMode.Tile>, but alternate columns of tiles are flipped horizontally.</span></span>  
  
-   <span data-ttu-id="25f2b-164"><xref:System.Windows.Media.TileMode.FlipY>: 同じ<xref:System.Windows.Media.TileMode.Tile>、が、タイルの代替の行が垂直方向に反転します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-164"><xref:System.Windows.Media.TileMode.FlipY>: The same as <xref:System.Windows.Media.TileMode.Tile>, but alternate rows of tiles are flipped vertically.</span></span>  
  
-   <span data-ttu-id="25f2b-165"><xref:System.Windows.Media.TileMode.FlipXY>: を組み合わせた<xref:System.Windows.Media.TileMode.FlipX>と<xref:System.Windows.Media.TileMode.FlipY>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-165"><xref:System.Windows.Media.TileMode.FlipXY>: A combination of <xref:System.Windows.Media.TileMode.FlipX> and <xref:System.Windows.Media.TileMode.FlipY>.</span></span>  
  
 <span data-ttu-id="25f2b-166">並べて表示するさまざまなモードを次のイメージに示します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-166">The following image illustrates the different tiling modes.</span></span>  
  
 <span data-ttu-id="25f2b-167">![TileBrush のさまざまな TileMode 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")</span><span class="sxs-lookup"><span data-stu-id="25f2b-167">![Different TileBrush TileMode settings](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")</span></span>  
  
 <span data-ttu-id="25f2b-168">次の例では、幅と高さが 100 ピクセルの四角形がイメージを使用して塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-168">In the following example, an image is used to paint a rectangle that is 100 pixels wide and 100 pixels tall.</span></span> <span data-ttu-id="25f2b-169">ブラシを設定して<xref:System.Windows.Media.TileBrush.Viewport%2A>が設定されている 0,0,0.25,0.25、するブラシの基本タイルが出力領域の 1/4 を作成します。</span><span class="sxs-lookup"><span data-stu-id="25f2b-169">By setting the brush's <xref:System.Windows.Media.TileBrush.Viewport%2A> has been set to 0,0,0.25,0.25, the brush's base tile is made to be 1/4 of the output area.</span></span> <span data-ttu-id="25f2b-170">ブラシの<xref:System.Windows.Media.TileBrush.TileMode%2A>に設定されている<xref:System.Windows.Media.TileMode.FlipXY>です。</span><span class="sxs-lookup"><span data-stu-id="25f2b-170">The brush's <xref:System.Windows.Media.TileBrush.TileMode%2A> is set to <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="25f2b-171">そのため、四角形はタイルの行で塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="25f2b-171">so that it fills the rectangle with rows of tiles.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a><span data-ttu-id="25f2b-172">参照</span><span class="sxs-lookup"><span data-stu-id="25f2b-172">See Also</span></span>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="25f2b-173">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="25f2b-173">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="25f2b-174">方法トピック</span><span class="sxs-lookup"><span data-stu-id="25f2b-174">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [<span data-ttu-id="25f2b-175">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="25f2b-175">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="25f2b-176">ImageBrush のサンプル</span><span class="sxs-lookup"><span data-stu-id="25f2b-176">ImageBrush Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [<span data-ttu-id="25f2b-177">VisualBrush のサンプル</span><span class="sxs-lookup"><span data-stu-id="25f2b-177">VisualBrush Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160049)
