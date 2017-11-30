---
title: "方法 : 複合図形を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ded7bd25f7f416bc512051f883b4ae12b2fa56d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-composite-shape"></a>方法 : 複合図形を作成する
この例を使用して複合図形を作成する方法を示します<xref:System.Windows.Media.Geometry>オブジェクトし、それらを表示を使用して、<xref:System.Windows.Shapes.Path>要素。 次の例で、 <xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.EllipseGeometry>、および<xref:System.Windows.Media.RectangleGeometry>で使用される、<xref:System.Windows.Media.GeometryGroup>複合図形を作成します。 ジオメトリを使用してを描画し、<xref:System.Windows.Shapes.Path>要素。  
  
## <a name="example"></a>例  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 前の例で作成した図を次に示します。  
  
 ![含む GeometryGroup を使用して作成された複合ジオメトリ](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
複合ジオメトリ  
  
 多角形、曲線のセグメントを含む図形などのより複雑な図形を使用して作成することがあります、<xref:System.Windows.Media.PathGeometry>です。 使用して、図形を作成する方法を示す例については、<xref:System.Windows.Media.PathGeometry>を参照してください[PathGeometry を使用して図形を作成](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)です。  この例では、画面を使用するための図形を表示します。 ただし、<xref:System.Windows.Shapes.Path>要素、<xref:System.Windows.Media.Geometry>の内容を記述するオブジェクトも使用できます、<xref:System.Windows.Media.GeometryDrawing>または<xref:System.Windows.Media.DrawingContext>です。 クリッピングとヒット テストも使用可能性があります。  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。
