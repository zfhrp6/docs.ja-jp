---
title: "方法 : 描画をイメージ ソースとして使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e0fe8f7d3633143348693c95d92dd2715bd0442
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="ef6f7-102">方法 : 描画をイメージ ソースとして使用する</span><span class="sxs-lookup"><span data-stu-id="ef6f7-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="ef6f7-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Drawing>として、<xref:System.Windows.Controls.Image.Source%2A>の<xref:System.Windows.Controls.Image>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ef6f7-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="ef6f7-104">表示する、<xref:System.Windows.Media.Drawing>で、<xref:System.Windows.Controls.Image>コントロールを使用して、<xref:System.Windows.Media.DrawingImage>として、<xref:System.Windows.Controls.Image>コントロールの<xref:System.Windows.Controls.Image.Source%2A>設定と、<xref:System.Windows.Media.DrawingImage>オブジェクトの<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>プロパティを表示する描画をします。</span><span class="sxs-lookup"><span data-stu-id="ef6f7-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef6f7-105">例</span><span class="sxs-lookup"><span data-stu-id="ef6f7-105">Example</span></span>  
 <span data-ttu-id="ef6f7-106">次の例では、<xref:System.Windows.Media.DrawingImage>と<xref:System.Windows.Controls.Image>を表示するコントロール、<xref:System.Windows.Media.GeometryDrawing>です。</span><span class="sxs-lookup"><span data-stu-id="ef6f7-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="ef6f7-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef6f7-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="ef6f7-108">![楕円 2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="ef6f7-108">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="ef6f7-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="ef6f7-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ef6f7-110">参照</span><span class="sxs-lookup"><span data-stu-id="ef6f7-110">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="ef6f7-111">ImageDrawing を使用してイメージを描画する</span><span class="sxs-lookup"><span data-stu-id="ef6f7-111">Draw an Image Using ImageDrawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [<span data-ttu-id="ef6f7-112">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="ef6f7-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="ef6f7-113">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="ef6f7-113">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="ef6f7-114">PresentationOptions:Freeze 属性</span><span class="sxs-lookup"><span data-stu-id="ef6f7-114">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
