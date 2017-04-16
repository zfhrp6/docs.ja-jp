---
title: "方法 : 3-D モデルのスケールを変換する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "3-D オブジェクト, スケーリング"
  - "スケーリング, 3-D オブジェクト"
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 方法 : 3-D モデルのスケールを変換する
この例では、3\-D オブジェクトをスケーリングする方法を示します。  3\-D オブジェクトをスケーリングするには、<xref:System.Windows.Media.Media3D.ScaleTransform3D> を使用します。  <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>、<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>、および <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> プロパティは、指定するファクターごとに要素のサイズを変更します。  たとえば、<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> の値が 1.5 である場合、オブジェクトは元の幅の 150% に引き伸ばされます。  <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> の値が 0.5 である場合、オブジェクトの高さは 50% 縮められます。  次のコードでは、<xref:System.Windows.Media.Media3D.GeometryModel3D> の変換として <xref:System.Windows.Media.Media3D.ScaleTransform3D> を使用する方法を示します。  
  
 [!code-xml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## 使用例  
 サンプル全体を次のコードに示します。  
  
 [!code-xml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## 参照  
 [3\-D 変換をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)   
 [3\-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)