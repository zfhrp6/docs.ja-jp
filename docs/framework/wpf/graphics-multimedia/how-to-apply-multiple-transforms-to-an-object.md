---
title: "方法 : オブジェクトに複数の変換を適用する | Microsoft Docs"
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
  - "グラフィックス, グループ化 (Transform オブジェクトを)"
  - "グループ化 (Transform オブジェクトを)"
  - "Transform オブジェクト, グループ化"
  - "TransformGroup"
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : オブジェクトに複数の変換を適用する
この例では、<xref:System.Windows.Media.TransformGroup> を使用して、2 つ以上の <xref:System.Windows.Media.Transform> オブジェクトを 1 つの複合 <xref:System.Windows.Media.Transform> にグループ化する方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.TransformGroup> を使用して、<xref:System.Windows.Media.ScaleTransform> と <xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Controls.Button> に適用します。  
  
 [!code-xml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.UIElement.RenderTransform%2A>   
 <xref:System.Windows.Media.TransformGroup>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)