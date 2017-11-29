---
title: "方法 : キー フレーム (QuaternionAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61968c13d395187d1190c7a2eaaa2bfe3f6072e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>方法 : キー フレーム (QuaternionAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する
次の例では、<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>回転 3D オブジェクトを作成するために使用します。 このアニメーションでは、次のキー フレームを使用します。  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>smooth、線形補間の作成に使用します。  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>突然「ジャンプ」(補間) の値の間の作成に使用されます。  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>によって値の間の変数の遷移の作成に使用される、<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>プロパティです。 次の例では、アニメーションのこの部分は低速と始まりますが、時間のセグメントの終了に向けて、指数関数的に速度が上がります。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [ストーリーボードを使用して 3-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Rotation3DAnimation を使用して 3-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [四元数を使用して 3-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [キー フレーム (Rotation3DAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
