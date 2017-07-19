---
title: "方法 : 3D シーンでカメラの位置および方向をアニメーション化する | Microsoft Docs"
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
  - "3-D シーン, アニメーション化 (カメラの方向を)"
  - "3-D シーン, アニメーション化 (カメラの位置を)"
  - "アニメーション, カメラの方向 (3-D シーンでの)"
  - "アニメーション, カメラの位置 (3-D シーンでの)"
  - "カメラの方向, アニメーション化 (3-D シーンでの)"
  - "カメラの位置, アニメーション化 (3-D シーンでの)"
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : 3D シーンでカメラの位置および方向をアニメーション化する
3D シーンでカメラの位置およびカメラが向いている方向をアニメーション化する方法を次の例に示します。  そのためには、<xref:System.Windows.Media.Animation.Point3DAnimation> と <xref:System.Windows.Media.Animation.Vector3DAnimation> を使用して、<xref:System.Windows.Media.Media3D.PerspectiveCamera> の <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> プロパティと <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> プロパティをそれぞれアニメーション化します。  この種のアニメーションは、イベントに対応して観察者が目にするシーンを変更するような場合に使用します。  
  
## 使用例  
 [!code-xml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>   
 <xref:System.Windows.Media.Animation.Point3DAnimation>   
 [キー フレームを使用してカメラの位置および方向をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)