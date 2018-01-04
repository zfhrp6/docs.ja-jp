---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)"
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
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5259e930060a8ac6118d232f08d02193a6a1b300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="d1a4a-102">方法 : パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)</span><span class="sxs-lookup"><span data-stu-id="d1a4a-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="d1a4a-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>クラスをパスに沿ってオブジェクトをアニメーション化し、そのオフセットを蓄積したアニメーションが繰り返される値します。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a4a-104">例</span><span class="sxs-lookup"><span data-stu-id="d1a4a-104">Example</span></span>  
 <span data-ttu-id="d1a4a-105">次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>ボタンに適用します。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="d1a4a-106">その結果、ボタンは曲線状のパスに沿って移動します。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="d1a4a-107">さらに、例では、設定、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>プロパティを`true`、それが原因で、アニメーションを繰り返すたびに蓄積するアニメーション化された行列のオフセット。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="d1a4a-108">オフセットが累積されるので、アニメーションが繰り返されたとき、ボタンは開始位置にリセットされるのではなく、画面を横切ってさらに移動します。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="d1a4a-109">なお、ですが、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>プロパティを繰り返しで累積する値をオフセットするとを蓄積する回転の値が原因です。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="d1a4a-110">回転の値を蓄積するために、設定、アニメーションの<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>と<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A>プロパティ`true`です。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="d1a4a-111">サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-111">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="d1a4a-112">アニメーション化する方法を示す例については、<xref:System.Windows.Media.Matrix>オフセット累積せずパスに沿った値は、「[オブジェクトに沿って、パス (行列アニメーション) をアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1a4a-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a4a-113">参照</span><span class="sxs-lookup"><span data-stu-id="d1a4a-113">See Also</span></span>  
 [<span data-ttu-id="d1a4a-114">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="d1a4a-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="d1a4a-115">パス アニメーションに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="d1a4a-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
