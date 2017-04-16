---
title: "方法 : 3-D 変換をアニメーション化する | Microsoft Docs"
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
  - "3-D 変換, アニメーション化"
  - "アニメーション, 3-D 変換"
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 3-D 変換をアニメーション化する
ここでは、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] モデルで設定された平行移動変換をアニメーション化する方法を説明します。  
  
 次のコードでは、<xref:System.Windows.Media.Media3D.TranslateTransform3D> オブジェクトを <xref:System.Windows.Media.Media3D.GeometryModel3D> の <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> プロパティに適用しています。  
  
 [!code-xml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 この <xref:System.Windows.Media.Media3D.TranslateTransform3D> オブジェクトの <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> プロパティは、次のコードを使用してアニメーション化されます。  
  
 [!code-xml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## 使用例  
 サンプル全体を次のコードに示します。  
  
 [!code-xml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [3\-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)