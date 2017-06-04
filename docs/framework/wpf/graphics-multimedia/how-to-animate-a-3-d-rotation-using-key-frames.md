---
title: "方法 : キー フレームを使用して 3-D 回転をアニメーション化する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "3-D 変換, アニメーション化, キー フレーム (Rotation3DAnimation) を使用"
  - "アニメーション, 3-D 変換, キー フレーム (Rotation3DAnimation) を使用"
  - "キー フレーム, Rotation3DAnimation"
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : キー フレームを使用して 3-D 回転をアニメーション化する
次の例では、<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> を使用し、回転の軸をアニメーション化することで "揺れている" ように見える 3D オブジェクトを回転させます。  このアニメーションでは、次のキー フレームを使用します。  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> は、値から値への滑らかで直線的な補間を作成するために使用します。  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> は、値から値への突然の "ジャンプ" \(補間なし\) を作成するために使用します。  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> は、<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> プロパティに従って、値から値への多様な遷移を作成するために使用します。  下の例で、この部分のアニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。  
  
## 使用例  
 [!code-xml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## 参照  
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [ストーリーボードを使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [Rotation3DAnimation を使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [四元数を使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)   
 [キー フレーム \(QuaternionAnimationUsingKeyFrames\) を使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)