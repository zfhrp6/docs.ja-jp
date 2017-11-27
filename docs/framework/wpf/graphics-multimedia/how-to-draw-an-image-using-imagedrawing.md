---
title: "方法 : ImageDrawing を使用してイメージを描画する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d975d33bb3c102e5294d78dc76d8136ab521953
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="1094e-102">方法 : ImageDrawing を使用してイメージを描画する</span><span class="sxs-lookup"><span data-stu-id="1094e-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="1094e-103">この例を使用する方法を示しています、<xref:System.Windows.Media.ImageDrawing>イメージを描画します。</span><span class="sxs-lookup"><span data-stu-id="1094e-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="1094e-104"><xref:System.Windows.Media.ImageDrawing>を表示できるように、<xref:System.Windows.Media.ImageSource>で、 <xref:System.Windows.Media.DrawingBrush>、 <xref:System.Windows.Media.DrawingImage>、または<xref:System.Windows.Media.Visual>です。</span><span class="sxs-lookup"><span data-stu-id="1094e-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="1094e-105">イメージを描画するを作成する、<xref:System.Windows.Media.ImageDrawing>設定とその<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1094e-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="1094e-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>プロパティを描画するイメージを指定して、<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>プロパティは、各イメージのサイズと位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="1094e-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1094e-107">例</span><span class="sxs-lookup"><span data-stu-id="1094e-107">Example</span></span>  
 <span data-ttu-id="1094e-108">次の例では、次の 4 つを使用して複合描画<xref:System.Windows.Media.ImageDrawing>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1094e-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="1094e-109">この例では、次の図が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1094e-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="1094e-110">![複数の DrawingImage オブジェクト](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="1094e-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="1094e-111">4 つの ImageDrawing オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1094e-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="1094e-112">使用せずにイメージを表示する簡単な方法を示す例については<xref:System.Windows.Media.ImageDrawing>を参照してください[イメージ要素を使用して](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="1094e-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1094e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1094e-113">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [<span data-ttu-id="1094e-114">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="1094e-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="1094e-115">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="1094e-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="1094e-116">PresentationOptions:Freeze 属性</span><span class="sxs-lookup"><span data-stu-id="1094e-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
