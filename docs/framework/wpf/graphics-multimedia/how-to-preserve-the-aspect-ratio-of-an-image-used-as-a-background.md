---
title: '方法 : 背景として使用するイメージの縦横比を保持する'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 906033b43ba657acc873f12a00000189db6796ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562717"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="bba41-102">方法 : 背景として使用するイメージの縦横比を保持する</span><span class="sxs-lookup"><span data-stu-id="bba41-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="bba41-103">この例を使用する方法を示しています、<xref:System.Windows.Media.TileBrush.Stretch%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>イメージの縦横比を維持するためにします。</span><span class="sxs-lookup"><span data-stu-id="bba41-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="bba41-104">既定では、使用すると、<xref:System.Windows.Media.ImageBrush>領域を塗りつぶすには、そのコンテンツ全体に引き伸ばす完全に、出力領域。</span><span class="sxs-lookup"><span data-stu-id="bba41-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="bba41-105">出力領域とイメージの縦横比が異なる場合は、この引き伸ばしによってイメージがゆがめられます。</span><span class="sxs-lookup"><span data-stu-id="bba41-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="bba41-106">させる、<xref:System.Windows.Media.ImageBrush>設定、そのイメージの縦横比を保持、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティを<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>です。</span><span class="sxs-lookup"><span data-stu-id="bba41-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba41-107">例</span><span class="sxs-lookup"><span data-stu-id="bba41-107">Example</span></span>  
 <span data-ttu-id="bba41-108">次の例を使用して 2 つ<xref:System.Windows.Media.ImageBrush>2 つの四角形を描画するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bba41-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="bba41-109">これらの四角形は 300 × 150 ピクセルで、どちらも 300 × 300 ピクセルのイメージを保持しています。</span><span class="sxs-lookup"><span data-stu-id="bba41-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="bba41-110"><xref:System.Windows.Media.TileBrush.Stretch%2A>最初のブラシのプロパティに設定されて<xref:System.Windows.Media.Stretch.Uniform>、および<xref:System.Windows.Media.TileBrush.Stretch%2A>2 番目のブラシのプロパティに設定されて<xref:System.Windows.Media.Stretch.UniformToFill>です。</span><span class="sxs-lookup"><span data-stu-id="bba41-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="bba41-111">次の図は、最初のブラシの出力、<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.Uniform>です。</span><span class="sxs-lookup"><span data-stu-id="bba41-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="bba41-112">![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="bba41-112">![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="bba41-113">次の図には、2 番目のブラシの出力、<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.UniformToFill>です。</span><span class="sxs-lookup"><span data-stu-id="bba41-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="bba41-114">![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="bba41-114">![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="bba41-115">なお、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティが、他の動作は同じです<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="bba41-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="bba41-116">詳細については<xref:System.Windows.Media.ImageBrush>と、その他の<xref:System.Windows.Media.TileBrush>、オブジェクトを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。</span><span class="sxs-lookup"><span data-stu-id="bba41-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="bba41-117">なおが、<xref:System.Windows.Media.TileBrush.Stretch%2A>を指定するプロパティが表示されます、<xref:System.Windows.Media.TileBrush>コンテンツは、その出力領域に合わせて拡大、実際に指定方法、<xref:System.Windows.Media.TileBrush>コンテンツの基本タイルをいっぱいに拡大します。</span><span class="sxs-lookup"><span data-stu-id="bba41-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="bba41-118">詳細については、「<xref:System.Windows.Media.TileBrush>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bba41-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="bba41-119">このコード例は提供されている長い例の一部である、<xref:System.Windows.Media.ImageBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="bba41-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="bba41-120">サンプル全体については、次を参照してください。 [ImageBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160005)です。</span><span class="sxs-lookup"><span data-stu-id="bba41-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba41-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="bba41-121">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="bba41-122">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="bba41-122">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
