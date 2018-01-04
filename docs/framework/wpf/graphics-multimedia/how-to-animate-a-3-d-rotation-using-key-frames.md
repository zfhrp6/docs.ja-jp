---
title: "方法 : キー フレームを使用して 3-D 回転をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca1b49277792e89f1d0cc7ca213d02978bb4dee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="5c5f8-102">方法 : キー フレームを使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="5c5f8-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="5c5f8-103">次の例では、 <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> 「補助」の結果として得られるその軸の回転をアニメーション化中に回転 3D オブジェクトを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="5c5f8-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="5c5f8-104">このアニメーションでは、次のキー フレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="5c5f8-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="5c5f8-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>smooth、線形補間の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="5c5f8-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="5c5f8-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>突然「ジャンプ」(補間) の値の間の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5c5f8-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="5c5f8-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>によって値の間の変数の遷移の作成に使用される、<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5c5f8-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="5c5f8-108">次の例では、アニメーションのこの部分は低速と始まりますが、時間のセグメントの終了に向けて、指数関数的に速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="5c5f8-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5f8-109">例</span><span class="sxs-lookup"><span data-stu-id="5c5f8-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5c5f8-110">参照</span><span class="sxs-lookup"><span data-stu-id="5c5f8-110">See Also</span></span>  
 [<span data-ttu-id="5c5f8-111">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="5c5f8-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="5c5f8-112">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="5c5f8-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="5c5f8-113">ストーリーボードを使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="5c5f8-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="5c5f8-114">Rotation3DAnimation を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="5c5f8-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="5c5f8-115">四元数を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="5c5f8-115">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="5c5f8-116">キー フレーム (QuaternionAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="5c5f8-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
