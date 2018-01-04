---
title: "方法 : 3D シーンでカメラの位置および方向をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8e80f1032e886d59240b74281c2ed87ad5743a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="3484a-102">方法 : 3D シーンでカメラの位置および方向をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="3484a-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="3484a-103">次の例では、カメラの位置をアニメーション化してが 3D シーンに向いている方向をアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3484a-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="3484a-104">使用してこれは、<xref:System.Windows.Media.Animation.Point3DAnimation>と<xref:System.Windows.Media.Animation.Vector3DAnimation>アニメーション化する、<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>と<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>それぞれのプロパティ、<xref:System.Windows.Media.Media3D.PerspectiveCamera>です。</span><span class="sxs-lookup"><span data-stu-id="3484a-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="3484a-105">次のように、アニメーションを使用して、イベントに応答内のシーンの観察のビューを変更する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3484a-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3484a-106">例</span><span class="sxs-lookup"><span data-stu-id="3484a-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3484a-107">参照</span><span class="sxs-lookup"><span data-stu-id="3484a-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [<span data-ttu-id="3484a-108">キー フレームを使用してカメラの位置および方向をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="3484a-108">Animate Camera Position and Direction Using Key Frames</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [<span data-ttu-id="3484a-109">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="3484a-109">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
