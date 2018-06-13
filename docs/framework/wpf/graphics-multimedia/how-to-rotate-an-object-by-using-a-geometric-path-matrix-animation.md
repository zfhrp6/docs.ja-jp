---
title: '方法 : ジオメトリック パスを使用してオブジェクトを回転させる (行列アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 6deb593ca059d49f744226be313adb6d8781b325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561990"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="5070c-102">方法 : ジオメトリック パスを使用してオブジェクトを回転させる (行列アニメーション)</span><span class="sxs-lookup"><span data-stu-id="5070c-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="5070c-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>と<xref:System.Windows.Media.MatrixTransform>(pivot) によって定義されたジオメトリック パスに沿ってオブジェクトを回転する、<xref:System.Windows.Media.PathGeometry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5070c-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5070c-104">例</span><span class="sxs-lookup"><span data-stu-id="5070c-104">Example</span></span>  
 <span data-ttu-id="5070c-105">次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。</span><span class="sxs-lookup"><span data-stu-id="5070c-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="5070c-106"><xref:System.Windows.Media.MatrixTransform>ボタンに適用され、曲線のパスに沿って移動する場合は、します。</span><span class="sxs-lookup"><span data-stu-id="5070c-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="5070c-107"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>プロパティに設定されている`true`、四角形がパスの接線に沿って回転します。</span><span class="sxs-lookup"><span data-stu-id="5070c-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="5070c-108">サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。</span><span class="sxs-lookup"><span data-stu-id="5070c-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="5070c-109">使用される前の例のコードのバージョン、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化する、 <xref:System.Windows.Media.EllipseGeometry>1 つだけのアニメーションが適用された場合でも、します。</span><span class="sxs-lookup"><span data-stu-id="5070c-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="5070c-110">コードでは、プロパティに 1 つのアニメーションを適用する簡単な方法が使用するには、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5070c-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="5070c-111">例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5070c-111">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5070c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5070c-112">See Also</span></span>  
 [<span data-ttu-id="5070c-113">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="5070c-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="5070c-114">パス アニメーションに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="5070c-114">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [<span data-ttu-id="5070c-115">パス アニメーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="5070c-115">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)
