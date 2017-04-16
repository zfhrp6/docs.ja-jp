---
title: "方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, カメラの方向をキー フレームで"
  - "アニメーション, カメラの位置をキー フレームで"
  - "カメラの方向, アニメーション化 (キー フレームを使用して)"
  - "カメラの位置, アニメーション化 (キー フレームを使用して)"
  - "キー フレーム, アニメーション化 (カメラの方向を)"
  - "キー フレーム, アニメーション化 (カメラの位置を)"
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する
次の例では、3D シーンでの <xref:System.Windows.Media.Media3D.PerspectiveCamera> の位置をアニメーション化するために <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> を使用しています。  また、3D シーンでカメラが向いている方向をアニメーション化するために <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> を使用しています。  どちらのアニメーションでも、一連のアニメーション効果を作成する複数のキー フレームを使用しています。  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> および <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> は、値間の滑らかな線形補間を作成するために使用します。  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> および <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> は、値間での突然の "ジャンプ" \(補間なし\) を作成するために使用します。  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> および <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> は、<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> プロパティに従って、値間の可変遷移を作成するために使用します。  次の例では、アニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。  
  
## 使用例  
 [!code-xml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## 参照  
 [3D シーンでカメラの位置および方向をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)