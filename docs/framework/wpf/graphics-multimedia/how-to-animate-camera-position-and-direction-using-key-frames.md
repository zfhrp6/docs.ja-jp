---
title: "方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06e815ddd8beb48f80f13d93604773079fcffa06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="bc889-102">方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="bc889-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="bc889-103">次の例では、<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>の位置をアニメーション化するために使用する<xref:System.Windows.Media.Media3D.PerspectiveCamera>3D シーンでします。</span><span class="sxs-lookup"><span data-stu-id="bc889-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="bc889-104">さらに、 <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> 3D シーンでカメラが指すの方向をアニメーション化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="bc889-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="bc889-105">これらのアニメーションの両方には、一連のアニメーション効果を作成するいくつかのキー フレームが使用します。</span><span class="sxs-lookup"><span data-stu-id="bc889-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1.  <span data-ttu-id="bc889-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>および<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>滑らかで線形補間を作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="bc889-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="bc889-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>および<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>突然「ジャンプ」(補間) の値の間の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="bc889-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="bc889-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>および<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>によって値の間の変数の遷移の作成に使用する、<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="bc889-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="bc889-109">次の例では、アニメーションは低速と始まりますが、時間のセグメントの末尾に向かって、指数関数的に速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="bc889-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc889-110">例</span><span class="sxs-lookup"><span data-stu-id="bc889-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bc889-111">参照</span><span class="sxs-lookup"><span data-stu-id="bc889-111">See Also</span></span>  
 [<span data-ttu-id="bc889-112">3D シーンでカメラの位置および方向をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="bc889-112">Animate Camera Position and Direction in a 3D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [<span data-ttu-id="bc889-113">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="bc889-113">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
