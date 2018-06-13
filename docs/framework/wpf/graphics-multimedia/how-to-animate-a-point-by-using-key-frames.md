---
title: '方法 : キー フレームを使用して点をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: a59ceb62d7feb33d2cc8a747a7bfb85e551d785c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557356"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="2bbfe-102">方法 : キー フレームを使用して点をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="2bbfe-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="2bbfe-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Point>です。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bbfe-104">例</span><span class="sxs-lookup"><span data-stu-id="2bbfe-104">Example</span></span>  
 <span data-ttu-id="2bbfe-105">次の例では、三角形のパスに沿って楕円を移動します。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="2bbfe-106">この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.EllipseGeometry.Center%2A>のプロパティ、<xref:System.Windows.Media.EllipseGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="2bbfe-107">このアニメーションは、次の方法で 3 つのキー フレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="2bbfe-108">最初の 0.5 秒中のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearPointKeyFrame>の開始位置から一定の割合でパスに沿った楕円を移動するクラス。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="2bbfe-109">などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearPointKeyFrame>値の間のスムーズな線形補間を作成します。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="2bbfe-110">インスタンスを使用している 0.5 秒は、次の終了時に、<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然パスに沿った楕円を次の位置に移動するクラス。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="2bbfe-111">などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>値間の突然のジャンプを作成します。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="2bbfe-112">最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplinePointKeyFrame>楕円の開始位置に移動するクラス。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="2bbfe-113">スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplinePointKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="2bbfe-114">この例では、アニメーションは最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="2bbfe-115">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-115">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="2bbfe-116">この例のコードを使用して他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>を適用するオブジェクト、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>です。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="2bbfe-117">ただし、コード内の 1 つのアニメーションを適用するときに使いやすく、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="2bbfe-118">例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bbfe-118">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbfe-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bbfe-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [<span data-ttu-id="2bbfe-120">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="2bbfe-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="2bbfe-121">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="2bbfe-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
