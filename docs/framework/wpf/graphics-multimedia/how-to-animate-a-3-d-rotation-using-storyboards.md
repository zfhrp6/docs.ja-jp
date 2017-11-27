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
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>方法 : ストーリーボードを使用して 3-D 回転をアニメーション化する
次の例は、中に「ぐらつく」アニメーションの回転の 3D オブジェクトを作成する方法を示しています、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>と<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>のプロパティ、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>オブジェクト。 これは、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>オブジェクトは、3 D のオブジェクトの回転変換を指定し、desire 回転効果を作成するためのプロパティをアニメーション化します。 ストーリー ボード内<xref:System.Windows.Media.Animation.DoubleAnimation>アニメーション化するために使用、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>中にプロパティ<xref:System.Windows.Media.Animation.Vector3DAnimation>アニメーション化するために使用、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>プロパティです。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [Rotation3DAnimation を使用して 3-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [キー フレーム (Rotation3DAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
