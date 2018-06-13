---
title: '方法 : キー フレーム (QuaternionAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 59514dcd617f73cc8c8e458dc13880b3521c0fb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557070"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="94b2f-102">方法 : キー フレーム (QuaternionAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="94b2f-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="94b2f-103">次の例では、<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>回転 3D オブジェクトを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="94b2f-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="94b2f-104">このアニメーションでは、次のキー フレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="94b2f-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="94b2f-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> smooth、線形補間の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="94b2f-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="94b2f-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> 突然「ジャンプ」(補間) の値の間の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="94b2f-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="94b2f-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> によって値の間の変数の遷移の作成に使用される、<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="94b2f-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="94b2f-108">次の例では、アニメーションのこの部分は低速と始まりますが、時間のセグメントの終了に向けて、指数関数的に速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="94b2f-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94b2f-109">例</span><span class="sxs-lookup"><span data-stu-id="94b2f-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="94b2f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="94b2f-110">See Also</span></span>  
 [<span data-ttu-id="94b2f-111">ストーリーボードを使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="94b2f-111">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="94b2f-112">Rotation3DAnimation を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="94b2f-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="94b2f-113">四元数を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="94b2f-113">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="94b2f-114">キー フレーム (Rotation3DAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="94b2f-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="94b2f-115">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="94b2f-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="94b2f-116">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="94b2f-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
