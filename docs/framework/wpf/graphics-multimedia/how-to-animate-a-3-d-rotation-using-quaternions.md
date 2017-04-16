---
title: "方法 : 四元数を使用して 3-D 回転をアニメーション化する | Microsoft Docs"
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
  - "3-D 変換, アニメーション化, 四元数を使用"
  - "アニメーション, 3-D 変換, 四元数を使用"
  - "四元数"
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : 四元数を使用して 3-D 回転をアニメーション化する
この例では、四元数を使用して 3\-D オブジェクトの回転をアニメーション化する方法を示します。  
  
 次のコードでは、<xref:System.Windows.Media.Media3D.RotateTransform3D> の <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> プロパティの値として使用される <xref:System.Windows.Media.Media3D.QuaternionRotation3D> を示します。  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 この <xref:System.Windows.Media.Media3D.QuaternionRotation3D> は、次のコードを使用して、<xref:System.Windows.Media.Animation.Storyboard> 内の <xref:System.Windows.Media.Animation.QuaternionAnimation> でアニメーション化されます。  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## 使用例  
 サンプル全体を次のコードに示します。  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [3\-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [ストーリーボードを使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [Rotation3DAnimation を使用して 3\-D 回転をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)