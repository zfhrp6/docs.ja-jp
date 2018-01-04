---
title: "方法 : 四元数を使用して 3-D 回転をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4301f4ffc935c6c72509638561ffa40b7744b94a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="32870-102">方法 : 四元数を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="32870-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="32870-103">この例では、四元数を使用して、3-D オブジェクトの回転をアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="32870-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="32870-104">次のコード、<xref:System.Windows.Media.Media3D.QuaternionRotation3D>の値として使用される、<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>のプロパティ、<xref:System.Windows.Media.Media3D.RotateTransform3D>です。</span><span class="sxs-lookup"><span data-stu-id="32870-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="32870-105">これは、<xref:System.Windows.Media.Media3D.QuaternionRotation3D>をアニメーション化、<xref:System.Windows.Media.Animation.QuaternionAnimation>内で、<xref:System.Windows.Media.Animation.Storyboard>次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="32870-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="32870-106">例</span><span class="sxs-lookup"><span data-stu-id="32870-106">Example</span></span>  
 <span data-ttu-id="32870-107">次のコードでは、全体のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="32870-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="32870-108">参照</span><span class="sxs-lookup"><span data-stu-id="32870-108">See Also</span></span>  
 [<span data-ttu-id="32870-109">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="32870-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="32870-110">3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="32870-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="32870-111">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="32870-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="32870-112">変換の概要</span><span class="sxs-lookup"><span data-stu-id="32870-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="32870-113">ストーリーボードを使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="32870-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="32870-114">Rotation3DAnimation を使用して 3-D 回転をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="32870-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
