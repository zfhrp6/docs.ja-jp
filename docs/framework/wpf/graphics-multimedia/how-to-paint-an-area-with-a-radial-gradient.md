---
title: '方法 : 放射状グラデーションを使用して領域を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: d794f85ce4968e1cf1759df5358834f3b4cdfb50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560643"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="66de1-102">方法 : 放射状グラデーションを使用して領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="66de1-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="66de1-103">この例を使用する方法を示しています、<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーションで領域を塗りつぶすクラス。</span><span class="sxs-lookup"><span data-stu-id="66de1-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66de1-104">例</span><span class="sxs-lookup"><span data-stu-id="66de1-104">Example</span></span>  
 <span data-ttu-id="66de1-105">次の例では、<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーション赤青の淡い緑から黄色から遷移を含む四角形を描画します。</span><span class="sxs-lookup"><span data-stu-id="66de1-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="66de1-106">次の図は、前の例からのグラデーションを示します。</span><span class="sxs-lookup"><span data-stu-id="66de1-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="66de1-107">グラデーションの終了位置が示されています。</span><span class="sxs-lookup"><span data-stu-id="66de1-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="66de1-108">![放射状グラデーションでのグラデーション境界](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="66de1-108">![Gradient stops in a radial gradient](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66de1-109">このトピックの例では、制御点を設定するための既定の座標系を使用します。</span><span class="sxs-lookup"><span data-stu-id="66de1-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="66de1-110">既定の座標システムは境界ボックスに対する相対: 0%、境界ボックスの場合は 0、1 は、境界ボックスの 100% を示します。</span><span class="sxs-lookup"><span data-stu-id="66de1-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="66de1-111">この座標系を変更するには設定して、<xref:System.Windows.Media.GradientBrush.MappingMode%2A>プロパティ値を<xref:System.Windows.Media.BrushMappingMode.Absolute>です。</span><span class="sxs-lookup"><span data-stu-id="66de1-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="66de1-112">絶対座標系は、境界ボックスに相対しません。</span><span class="sxs-lookup"><span data-stu-id="66de1-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="66de1-113">値は、ローカル空間に直接変換されます。</span><span class="sxs-lookup"><span data-stu-id="66de1-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="66de1-114">追加<xref:System.Windows.Media.RadialGradientBrush>例についてを参照してください、[ブラシ サンプル](http://go.microsoft.com/fwlink/?LinkID=159973)です。</span><span class="sxs-lookup"><span data-stu-id="66de1-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="66de1-115">グラデーションおよびその他の種類のブラシの詳細については、次を参照してください。[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="66de1-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
