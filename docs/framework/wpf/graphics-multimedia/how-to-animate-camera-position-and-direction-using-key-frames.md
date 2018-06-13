---
title: '方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 5be14513755c3b5c80c13cbc5cae889cc4663cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558840"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する
次の例では、<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>の位置をアニメーション化するために使用する<xref:System.Windows.Media.Media3D.PerspectiveCamera>3D シーンでします。 さらに、 <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> 3D シーンでカメラが指すの方向をアニメーション化するために使用します。 これらのアニメーションの両方には、一連のアニメーション効果を作成するいくつかのキー フレームが使用します。  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> および<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>滑らかで線形補間を作成するために使用します。  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> および<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>突然「ジャンプ」(補間) の値の間の作成に使用します。  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> および<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>によって値の間の変数の遷移の作成に使用する、<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>プロパティです。 次の例では、アニメーションは低速と始まりますが、時間のセグメントの末尾に向かって、指数関数的に速度が上がります。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [3D シーンでカメラの位置および方向をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
