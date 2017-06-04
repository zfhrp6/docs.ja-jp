---
title: "方法 : 3-D シーンで素材プロパティをアニメーション化する | Microsoft Docs"
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
  - "3-D シーン, アニメーション化 (素材プロパティを)"
  - "アニメーション, 素材プロパティ (3-D シーンの)"
  - "素材プロパティ, アニメーション化 (3-D シーンでの)"
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 3-D シーンで素材プロパティをアニメーション化する
次の例は、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] モデルに適用された <xref:System.Windows.Media.Media3D.Material> の <xref:System.Windows.Media.Brush.Opacity%2A> プロパティにアニメーションを適用する方法を示しています。  
  
 3D オブジェクトに適用する <xref:System.Windows.Media.Media3D.Material> として使用される <xref:System.Windows.Media.LinearGradientBrush> を定義するコード例を次に示します。  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 この <xref:System.Windows.Media.LinearGradientBrush> の <xref:System.Windows.Media.Brush.Opacity%2A> プロパティは、次のコード例を使用してアニメーション化されます。  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## 使用例  
 サンプル全体を次のコードに示します。  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## 参照  
 [3\-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)