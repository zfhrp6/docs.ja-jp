---
title: "方法 : 3-D モデルに描画を適用する | Microsoft Docs"
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
  - "3-D モデル, 適用 (描画を)"
  - "描画, 適用 (3-D モデルに)"
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 3-D モデルに描画を適用する
<xref:System.Windows.Media.DrawingBrush> を、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] モデルに適用された <xref:System.Windows.Media.Media3D.Material> として使用する方法を次の例に示します。  
  
 次のコードは、<xref:System.Windows.Media.DrawingGroup> を <xref:System.Windows.Media.DrawingBrush> のコンテンツとして定義しています。  <xref:System.Windows.Media.DrawingBrush> は、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 平面に適用された <xref:System.Windows.Media.Media3D.DiffuseMaterial> の <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> プロパティとして設定されています。  
  
 **メモ :** 下記の描画のように複雑なオブジェクトや値は、再利用が可能なリソースとして定義して、コードを簡略化することを推奨します。  詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 [!code-xml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## 使用例  
 サンプル全体を次のコードに示します。  
  
 [!code-xml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## 参照  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [3\-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)