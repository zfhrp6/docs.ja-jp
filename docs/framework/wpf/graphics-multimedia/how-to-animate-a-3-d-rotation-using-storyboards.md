---
title: "方法 : ストーリーボードを使用して 3-D 回転をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56839dfc5382f5dd56ec0b26d4aabe42536bf04e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="9180c-102">方法 : ストーリーボードを使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="9180c-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="9180c-103">次の例は、中に「ぐらつく」アニメーションの回転の 3D オブジェクトを作成する方法を示しています、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>と<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>のプロパティ、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9180c-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="9180c-104">これは、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>オブジェクトは、3 D のオブジェクトの回転変換を指定し、desire 回転効果を作成するためのプロパティをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="9180c-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="9180c-105">ストーリー ボード内<xref:System.Windows.Media.Animation.DoubleAnimation>アニメーション化するために使用、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>中にプロパティ<xref:System.Windows.Media.Animation.Vector3DAnimation>アニメーション化するために使用、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9180c-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9180c-106">例</span><span class="sxs-lookup"><span data-stu-id="9180c-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9180c-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="9180c-107">See Also</span></span>  
 [<span data-ttu-id="9180c-108">Rotation3DAnimation を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="9180c-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="9180c-109">キー フレーム (Rotation3DAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="9180c-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="9180c-110">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="9180c-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="9180c-111">ストーリーボードの概要</span><span class="sxs-lookup"><span data-stu-id="9180c-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
