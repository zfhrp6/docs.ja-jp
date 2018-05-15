---
title: '方法 : ビジュアルからビットマップを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 4735474d00712598cb5e41fad289e8f568d83a48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="eb0ae-102">方法 : ビジュアルからビットマップを作成する</span><span class="sxs-lookup"><span data-stu-id="eb0ae-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="eb0ae-103">この例からビットマップを作成する方法、<xref:System.Windows.Media.Visual>です。</span><span class="sxs-lookup"><span data-stu-id="eb0ae-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="eb0ae-104">A<xref:System.Windows.Media.DrawingVisual>でレンダリングされて<xref:System.Windows.Media.FormattedText>です。</span><span class="sxs-lookup"><span data-stu-id="eb0ae-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="eb0ae-105"><xref:System.Windows.Media.Visual>にレンダリングし、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>指定されたテキストのビットマップを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb0ae-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb0ae-106">例</span><span class="sxs-lookup"><span data-stu-id="eb0ae-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="eb0ae-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb0ae-107">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="eb0ae-108">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="eb0ae-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="eb0ae-109">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="eb0ae-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="eb0ae-110">DrawingVisual オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="eb0ae-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
