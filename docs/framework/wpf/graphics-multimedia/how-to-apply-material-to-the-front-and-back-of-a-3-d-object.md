---
title: "方法 : 3-D オブジェクトの前面および背面に素材を適用する | Microsoft Docs"
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
  - "3-D オブジェクト, 適用 (Material クラスを)"
  - "クラス, 質感"
  - "Material クラス, 適用 (3-D オブジェクトの両側に)"
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : 3-D オブジェクトの前面および背面に素材を適用する
<xref:System.Windows.Media.Media3D.Material> を 3\-D オブジェクトの前面と背面に適用し、オブジェクトの両側を見せるようにアニメーション化する方法を次の例に示します。  <xref:System.Windows.Media.Media3D.GeometryModel3D> の <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> プロパティを使用して、オブジェクトの前面に赤い <xref:System.Windows.Media.Brush> を適用し、<xref:System.Windows.Media.Media3D.GeometryModel3D> の <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> プロパティを使用して、オブジェクトの背面に青い <xref:System.Windows.Media.Brush> を適用しています。  次のコードでは、素材をオブジェクトに適用しています。  
  
 [!code-xml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## 使用例  
 サンプル全体を次のコードに示します。  
  
 [!code-xml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## 参照  
 [3\-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [3\-D シーンで素材プロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)   
 [3\-D モデルに放射性素材を適用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)