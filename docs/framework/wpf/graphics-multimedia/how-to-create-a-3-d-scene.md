---
title: "方法 : 3-D シーンを作成する | Microsoft Docs"
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
  - "3-D シーン"
  - "作成, 3-D シーン"
  - "シーン, 3-D"
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 3-D シーンを作成する
この例では、平らな紙を回転させたような 3\-D オブジェクトを作成する方法を示します。  <xref:System.Windows.Controls.Viewport3D> を次のコンポーネントと共に使用して、この簡単な 3\-D シーンを作成します。  
  
-   カメラは、<xref:System.Windows.Media.Media3D.PerspectiveCamera> を使用して作成します。  カメラは、3\-D シーンの表示する部分を指定します。  
  
-   メッシュは、<xref:System.Windows.Media.Media3D.GeometryModel3D> の <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> プロパティを使用して作成し、3\-D オブジェクト \(紙\) の形状を指定します。  
  
-   マテリアルは、<xref:System.Windows.Media.Media3D.GeometryModel3D> の <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> プロパティを使用して指定し、オブジェクト \(この例では線形グラデーション\) のサーフェイスに表示されます。  
  
-   光源は、<xref:System.Windows.Media.Media3D.DirectionalLight> を使用して作成し、オブジェクトに光を当てます。  
  
## 使用例  
 次のコードでは、3\-D シーンを XAML で作成する方法を示します。  
  
 [!code-xml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## 使用例  
 次のコードでは、同じ 3\-D シーンを手順コードで作成する方法を示します。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## 参照  
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)