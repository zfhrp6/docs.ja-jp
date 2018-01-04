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
ms.workload: dotnet
ms.openlocfilehash: 2ecb4ecdc5c83cbb6f2b4faee9cb3654939bd346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="b7240-102">方法 : 複合図形を作成する</span><span class="sxs-lookup"><span data-stu-id="b7240-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="b7240-103">この例を使用して複合図形を作成する方法を示します<xref:System.Windows.Media.Geometry>オブジェクトし、それらを表示を使用して、<xref:System.Windows.Shapes.Path>要素。</span><span class="sxs-lookup"><span data-stu-id="b7240-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="b7240-104">次の例で、 <xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.EllipseGeometry>、および<xref:System.Windows.Media.RectangleGeometry>で使用される、<xref:System.Windows.Media.GeometryGroup>複合図形を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7240-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="b7240-105">ジオメトリを使用してを描画し、<xref:System.Windows.Shapes.Path>要素。</span><span class="sxs-lookup"><span data-stu-id="b7240-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7240-106">例</span><span class="sxs-lookup"><span data-stu-id="b7240-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="b7240-107">前の例で作成した図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b7240-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="b7240-108">![含む GeometryGroup を使用して作成された複合ジオメトリ](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="b7240-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="b7240-109">複合ジオメトリ</span><span class="sxs-lookup"><span data-stu-id="b7240-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="b7240-110">多角形、曲線のセグメントを含む図形などのより複雑な図形を使用して作成することがあります、<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="b7240-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="b7240-111">使用して、図形を作成する方法を示す例については、<xref:System.Windows.Media.PathGeometry>を参照してください[PathGeometry を使用して図形を作成](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)です。</span><span class="sxs-lookup"><span data-stu-id="b7240-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="b7240-112">この例では、画面を使用するための図形を表示します。 ただし、<xref:System.Windows.Shapes.Path>要素、<xref:System.Windows.Media.Geometry>の内容を記述するオブジェクトも使用できます、<xref:System.Windows.Media.GeometryDrawing>または<xref:System.Windows.Media.DrawingContext>です。</span><span class="sxs-lookup"><span data-stu-id="b7240-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="b7240-113">クリッピングとヒット テストも使用可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b7240-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="b7240-114">この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7240-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
