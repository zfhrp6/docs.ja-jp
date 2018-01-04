---
title: "方法 : 直線または線分の終点のキャップを変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d2cd55de403b766344749259068ccd313558f89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="36bd5-102">方法 : 直線または線分の終点のキャップを変更する</span><span class="sxs-lookup"><span data-stu-id="36bd5-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="36bd5-103">この例は、開始のまたは末尾に、開いている図形を変更する方法を示します<xref:System.Windows.Shapes.Shape>要素。</span><span class="sxs-lookup"><span data-stu-id="36bd5-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="36bd5-104">開いているの先頭に cap を変更する<xref:System.Windows.Shapes.Shape>を使用してその<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="36bd5-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="36bd5-105">開いているの最後に、cap を変更する<xref:System.Windows.Shapes.Shape>を使用してその<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="36bd5-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="36bd5-106">使用可能なライン キャップを表示するを参照してください。、<xref:System.Windows.Media.PenLineCap>列挙します。</span><span class="sxs-lookup"><span data-stu-id="36bd5-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36bd5-107">このプロパティは、開いている図形など、 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Polyline>、または開いている<xref:System.Windows.Shapes.Path>要素。</span><span class="sxs-lookup"><span data-stu-id="36bd5-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="36bd5-108">次の例では、次の 4 つを描画<xref:System.Windows.Shapes.Polyline>要素の各端に別の図形のセットを使用しています。</span><span class="sxs-lookup"><span data-stu-id="36bd5-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36bd5-109">例</span><span class="sxs-lookup"><span data-stu-id="36bd5-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="36bd5-110">この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。</span><span class="sxs-lookup"><span data-stu-id="36bd5-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bd5-111">参照</span><span class="sxs-lookup"><span data-stu-id="36bd5-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
