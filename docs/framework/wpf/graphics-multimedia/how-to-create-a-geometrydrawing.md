---
title: "方法 : GeometryDrawing を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31417a3eeee2c1e61674c43558c2799705797c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-geometrydrawing"></a>方法 : GeometryDrawing を作成する
この例を作成し、表示する方法を示しています、<xref:System.Windows.Media.GeometryDrawing>です。 A<xref:System.Windows.Media.GeometryDrawing>を関連付けることで作成して、アウトラインの図形を作成することができます、<xref:System.Windows.Media.Pen>と<xref:System.Windows.Media.Brush>で、<xref:System.Windows.Media.Geometry>です。 <xref:System.Windows.Media.GeometryDrawing.Geometry%2A>図形の構造について説明します、 <xref:System.Windows.Media.GeometryDrawing.Brush%2A> 、図形の塗りつぶしをについて説明し、<xref:System.Windows.Media.GeometryDrawing.Pen%2A>図形の輪郭をについて説明します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.GeometryDrawing>図形を表示するためにします。 図形は、<xref:System.Windows.Media.GeometryGroup>と 2 つ<xref:System.Windows.Media.EllipseGeometry>オブジェクト。 図形の内部を描画すると、<xref:System.Windows.Media.LinearGradientBrush>でアウトラインを描画し、 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>です。 <xref:System.Windows.Media.GeometryDrawing>を使用して、表示、<xref:System.Windows.Media.ImageDrawing>と<xref:System.Windows.Controls.Image>要素。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 次の図は、結果として得られる<xref:System.Windows.Media.GeometryDrawing>です。  
  
 ![楕円 2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 複雑な図面を作成するには、描画を使用して 1 つの複合に複数の描画オブジェクトを結合できます、<xref:System.Windows.Media.DrawingGroup>です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.DrawingGroup>  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [複合描画を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
