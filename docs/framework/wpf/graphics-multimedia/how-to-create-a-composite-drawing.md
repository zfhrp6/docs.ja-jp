---
title: "方法 : 複合描画を作成する | Microsoft Docs"
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
  - "クラス, DrawingGroup"
  - "複合描画"
  - "DrawingGroup クラス"
  - "描画, 複合"
  - "グラフィックス, 複合描画"
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 複合描画を作成する
この例では、<xref:System.Windows.Media.DrawingGroup> を使用して複数の <xref:System.Windows.Media.Drawing> オブジェクトを 1 つの複合描画に結合することで複雑な描画を作成する方法を説明します。  
  
## 使用例  
 <xref:System.Windows.Media.DrawingGroup> を使用して <xref:System.Windows.Media.GeometryDrawing> オブジェクトと <xref:System.Windows.Media.ImageDrawing> オブジェクトから複合描画を作成する例を次に示します。  この例が生成する出力を次の図に示します。  
  
 ![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.png "graphicsmm\_simple")  
DrawingGroup を使用して作成した複合描画  
  
 描画の境界を表す灰色の境界線に注目してください。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup> を使用して、<xref:System.Windows.Media.DrawingGroup.Transform%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A> の設定、<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、または <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> を、グループに含まれる描画に適用できます。  <xref:System.Windows.Media.DrawingGroup> は <xref:System.Windows.Media.Drawing> でもあるため、他の <xref:System.Windows.Media.DrawingGroup> オブジェクトを含めることができます。  
  
 次の例は前の例と似ていますが、追加の <xref:System.Windows.Media.DrawingGroup> オブジェクトを使用して、ビットマップ効果と不透明マスクを一部の描画に適用している点が異なります。  この例が生成する出力を次の図に示します。  
  
 ![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.png "graphicsmm\_multiple")  
複数の DrawingGroup オブジェクトを使用する複合描画  
  
 描画の境界を表す灰色の境界線に注目してください。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <xref:System.Windows.Media.Drawing> オブジェクトの詳細については、「[Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>   
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>   
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>   
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>   
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>   
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)