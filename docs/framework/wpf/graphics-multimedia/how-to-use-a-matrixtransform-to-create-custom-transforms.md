---
title: "方法 : MatrixTransform を使用してカスタム変換を作成する | Microsoft Docs"
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
  - "クラス, MatrixTransform"
  - "グラフィックス [WPF], カスタム変換"
  - "MatrixTransform クラス"
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : MatrixTransform を使用してカスタム変換を作成する
この例では、<xref:System.Windows.Media.MatrixTransform> を使用して、<xref:System.Windows.Controls.Button> の位置、伸縮、および[傾斜](GTMT)を変換 \(移動\) する方法を示します。  
  
> [!NOTE]
>  <xref:System.Windows.Media.RotateTransform>、<xref:System.Windows.Media.SkewTransform>、<xref:System.Windows.Media.ScaleTransform>、または <xref:System.Windows.Media.TranslateTransform> の各クラスでは提供されないカスタム変換を作成するには、<xref:System.Windows.Media.MatrixTransform> クラスを使用します。  
  
## 使用例  
 [!code-xml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## 参照  
 <xref:System.Windows.Media.MatrixTransform>   
 <xref:System.Windows.Media.Transform>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)