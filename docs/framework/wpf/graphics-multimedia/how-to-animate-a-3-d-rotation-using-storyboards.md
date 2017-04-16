---
title: "方法 : ストーリーボードを使用して 3-D 回転をアニメーション化する | Microsoft Docs"
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
  - "3-D 変換, アニメーション化, ストーリーボードで"
  - "アニメーション, 3-D 変換, ストーリーボードで"
  - "ストーリーボード"
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ストーリーボードを使用して 3-D 回転をアニメーション化する
<xref:System.Windows.Media.Media3D.AxisAngleRotation3D> オブジェクトの <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> プロパティと <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> プロパティをアニメーション化することで、"揺れている" 3D オブジェクトを回転させる方法を次の例に示します。  この <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> オブジェクトは 3D オブジェクトの回転変換を指定しているため、そのプロパティをアニメーション化すると、目的の回転効果が作成されます。  ストーリーボード内では、<xref:System.Windows.Media.Animation.Vector3DAnimation> を使用して <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> プロパティをアニメーション化している間に、<xref:System.Windows.Media.Animation.DoubleAnimation> を使用して <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> プロパティをアニメーション化します。  
  
## 使用例  
 [!code-xml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## 参照  
 [Rotation3DAnimation を使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [キー フレーム \(Rotation3DAnimationUsingKeyFrames\) を使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)