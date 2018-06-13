---
title: '方法 : ブラシを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: 5caa00a378101ff4dff7745a18c3ec8905cc168b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561604"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="0446b-102">方法 : ブラシを変換する</span><span class="sxs-lookup"><span data-stu-id="0446b-102">How to: Transform a Brush</span></span>
<span data-ttu-id="0446b-103">この例は、変換する方法を示しています。 <xref:System.Windows.Media.Brush> 、2 つの変換のプロパティを使用して、オブジェクト:<xref:System.Windows.Media.Brush.RelativeTransform%2A>と<xref:System.Windows.Media.Brush.Transform%2A>です。</span><span class="sxs-lookup"><span data-stu-id="0446b-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="0446b-104">次の例を使用して、<xref:System.Windows.Media.RotateTransform>の内容を回転する、<xref:System.Windows.Media.ImageBrush>で 45 度。</span><span class="sxs-lookup"><span data-stu-id="0446b-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="0446b-105">次の図は、<xref:System.Windows.Media.ImageBrush>せず、<xref:System.Windows.Media.RotateTransform>で、<xref:System.Windows.Media.RotateTransform>に適用される、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティを使用して、<xref:System.Windows.Media.RotateTransform>に適用される、<xref:System.Windows.Media.Brush.Transform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0446b-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="0446b-106">![ブラシの RelativeTransform と Transform の設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="0446b-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="0446b-107">例</span><span class="sxs-lookup"><span data-stu-id="0446b-107">Example</span></span>  
 <span data-ttu-id="0446b-108">最初の例に適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.Brush.RelativeTransform%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>です。</span><span class="sxs-lookup"><span data-stu-id="0446b-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="0446b-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>オブジェクトは、このコンテンツの中心点の相対座標を 0.5 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="0446b-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="0446b-110">その結果、<xref:System.Windows.Media.ImageBrush>コンテンツがその中心を中心として回転します。</span><span class="sxs-lookup"><span data-stu-id="0446b-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="0446b-111">2 番目の例も適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.ImageBrush>。 ただし、この例では、<xref:System.Windows.Media.Brush.Transform%2A>プロパティの代わりに、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0446b-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="0446b-112">ブラシ中心の周りの回転、設定、<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>絶対座標するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0446b-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="0446b-113">このブラシは、175 x 90 ピクセルの四角形を描画するため、四角形の中心点は (87.5, 45) になります。</span><span class="sxs-lookup"><span data-stu-id="0446b-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="0446b-114">方法の詳細については<xref:System.Windows.Media.Brush.RelativeTransform%2A>と<xref:System.Windows.Media.Brush.Transform%2A>プロパティが動作しを参照してください、[ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="0446b-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="0446b-115">完全なサンプルについては、「[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0446b-115">For the complete sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="0446b-116">ブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0446b-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0446b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0446b-117">See Also</span></span>  
 [<span data-ttu-id="0446b-118">ブラシの変換の概要</span><span class="sxs-lookup"><span data-stu-id="0446b-118">Brush Transformation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [<span data-ttu-id="0446b-119">純色およびグラデーションによる塗りつぶしの概要</span><span class="sxs-lookup"><span data-stu-id="0446b-119">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="0446b-120">変換の概要</span><span class="sxs-lookup"><span data-stu-id="0446b-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
