---
title: '方法 : キー フレームを使用して四角形のジオメトリをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 581dc89d21091ad0ce856d7a7ced84fd7bcea9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="f18eb-102">方法 : キー フレームを使用して四角形のジオメトリをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="f18eb-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="f18eb-103">この例は、アニメーション化する方法を示しています。、<xref:System.Windows.Media.RectangleGeometry.Rect%2A>のプロパティ、<xref:System.Windows.Media.RectangleGeometry>キー フレームを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f18eb-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18eb-104">例</span><span class="sxs-lookup"><span data-stu-id="f18eb-104">Example</span></span>  
 <span data-ttu-id="f18eb-105">次の例では、<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.RectangleGeometry.Rect%2A>のプロパティ、<xref:System.Windows.Media.RectangleGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="f18eb-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="f18eb-106">このアニメーションは、次の方法で 3 つのキー フレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="f18eb-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="f18eb-107">最初の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.LinearRectKeyFrame>位置、幅、および四角形の高さの段階的な変更をアニメーション化するクラス。</span><span class="sxs-lookup"><span data-stu-id="f18eb-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="f18eb-108">などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearRectKeyFrame>値の間のスムーズな線形遷移を作成します。</span><span class="sxs-lookup"><span data-stu-id="f18eb-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="f18eb-109">インスタンスを使用している 0.5 秒は、次の終了時に、<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>突然四角形の高さを低くクラス。</span><span class="sxs-lookup"><span data-stu-id="f18eb-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="f18eb-110">などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>されている値の間での急激な変化を作成、高さの減少が迅速に行われ、微妙ではありません。</span><span class="sxs-lookup"><span data-stu-id="f18eb-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="f18eb-111">最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplineRectKeyFrame>四角形を元の位置とサイズに変更するクラス。</span><span class="sxs-lookup"><span data-stu-id="f18eb-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="f18eb-112">スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineRectKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f18eb-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="f18eb-113">この例では、変化は最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。</span><span class="sxs-lookup"><span data-stu-id="f18eb-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f18eb-114">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f18eb-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18eb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f18eb-115">See Also</span></span>  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [<span data-ttu-id="f18eb-116">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="f18eb-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f18eb-117">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="f18eb-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
