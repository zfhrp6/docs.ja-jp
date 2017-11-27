---
title: "方法 : 要素を傾斜させる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5c46b8c64a26d83ba6d8f018b9a1f8ca8250a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="33cd1-102">方法 : 要素を傾斜させる</span><span class="sxs-lookup"><span data-stu-id="33cd1-102">How to: Skew an Element</span></span>
<span data-ttu-id="33cd1-103">この例を使用する方法を示しています、<xref:System.Windows.Media.SkewTransform>要素を傾けるにします。</span><span class="sxs-lookup"><span data-stu-id="33cd1-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="33cd1-104">傾斜 (スキューと呼ばれることもあります) は、一様でない方法で座標空間を拡大する変換です。</span><span class="sxs-lookup"><span data-stu-id="33cd1-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="33cd1-105">一般的な用途の 1 つ、<xref:System.Windows.Media.SkewTransform>をシミュレートするため、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]で深さ[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="33cd1-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="33cd1-106">使用して、<xref:System.Windows.Media.SkewTransform.CenterX%2A>と<xref:System.Windows.Media.SkewTransform.CenterY%2A>のポイントを中心に指定のプロパティ、<xref:System.Windows.Media.SkewTransform>です。</span><span class="sxs-lookup"><span data-stu-id="33cd1-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="33cd1-107">使用して、<xref:System.Windows.Media.SkewTransform.AngleX%2A>と<xref:System.Windows.Media.SkewTransform.AngleY%2A>プロパティを x 軸と y 軸の傾斜角度を指定し、現在の座標系これらの軸に沿った傾斜をします。</span><span class="sxs-lookup"><span data-stu-id="33cd1-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="33cd1-108">傾斜変換の効果を予測することを検討<xref:System.Windows.Media.SkewTransform.AngleX%2A>元の座標システムに対して相対的な x 軸の値のずれ。</span><span class="sxs-lookup"><span data-stu-id="33cd1-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="33cd1-109">そのため、 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30、y 軸原点を 30 度回転し、傾斜 x-30 ° を原点からの値。</span><span class="sxs-lookup"><span data-stu-id="33cd1-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="33cd1-110">同様に、 <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 の原点から 30 度、図形の y 値のずれ。</span><span class="sxs-lookup"><span data-stu-id="33cd1-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="33cd1-111">これは、座標系の x または y での 30 度の平行移動 (移動) と同じ効果はないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="33cd1-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="33cd1-112">次の例に 45 度の水平方向の傾斜を適用する、 <xref:System.Windows.Shapes.Rectangle> (0, 0) の中心点からです。</span><span class="sxs-lookup"><span data-stu-id="33cd1-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33cd1-113">例</span><span class="sxs-lookup"><span data-stu-id="33cd1-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="33cd1-114">次の例に 45 度の水平方向の傾斜を適用する、 <xref:System.Windows.Shapes.Rectangle> (25,25) の中心点からです。</span><span class="sxs-lookup"><span data-stu-id="33cd1-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="33cd1-115">次の例に 45 度の垂直方向の傾斜を適用する、 <xref:System.Windows.Shapes.Rectangle> (25,25) の中心点からです。</span><span class="sxs-lookup"><span data-stu-id="33cd1-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="33cd1-116">次の図は、この例で使用されている各種の傾斜を示しています。</span><span class="sxs-lookup"><span data-stu-id="33cd1-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="33cd1-117">![SkewTransform の例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="33cd1-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="33cd1-118">説明した 3 つの SkewTransform の例</span><span class="sxs-lookup"><span data-stu-id="33cd1-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="33cd1-119">完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33cd1-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33cd1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="33cd1-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="33cd1-121">変換の概要</span><span class="sxs-lookup"><span data-stu-id="33cd1-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="33cd1-122">方法トピック</span><span class="sxs-lookup"><span data-stu-id="33cd1-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
