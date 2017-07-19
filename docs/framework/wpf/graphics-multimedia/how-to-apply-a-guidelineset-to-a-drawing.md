---
title: "方法 : 描画に GuidelineSet を適用する | Microsoft Docs"
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
  - "グラフィックス [WPF], GuidelineSet プロパティ"
  - "GuidelineSet プロパティ, 適用 (描画に)"
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 描画に GuidelineSet を適用する
この例では、<xref:System.Windows.Media.GuidelineSet> を <xref:System.Windows.Media.DrawingGroup> に適用する方法を示します。  
  
 <xref:System.Windows.Media.DrawingGroup> クラスは、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> プロパティを持つ <xref:System.Windows.Media.Drawing> の唯一の型です。  <xref:System.Windows.Media.GuidelineSet> を <xref:System.Windows.Media.Drawing> の別の型に適用するには、その型を <xref:System.Windows.Media.DrawingGroup> に追加した後、<xref:System.Windows.Media.GuidelineSet> を <xref:System.Windows.Media.DrawingGroup> に適用します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.DrawingGroup> オブジェクトを 2 つ作成します。両者はほとんど同じですが、唯一異なっているのは、2 番目の <xref:System.Windows.Media.DrawingGroup> が <xref:System.Windows.Media.GuidelineSet> を持っているのに対し、1 番目は持っていないことです。  
  
 この例からの出力を次の図に示します。  2 つの <xref:System.Windows.Media.DrawingGroup> オブジェクトのレンダリングの違いはごくわずかなので、描画の一部を拡大してあります。  
  
 ![GuidelineSet がある &#40;またはない&#41; DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm\_drawinggroup\_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.Media.DrawingGroup>   
 <xref:System.Windows.Media.GuidelineSet>   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)