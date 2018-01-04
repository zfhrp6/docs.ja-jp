---
title: "方法 : ビジュアルからビットマップを作成する"
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
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db3ad547072f1d9162ede5c45144aa30e809c50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="e43d1-102">方法 : ビジュアルからビットマップを作成する</span><span class="sxs-lookup"><span data-stu-id="e43d1-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="e43d1-103">この例からビットマップを作成する方法、<xref:System.Windows.Media.Visual>です。</span><span class="sxs-lookup"><span data-stu-id="e43d1-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="e43d1-104">A<xref:System.Windows.Media.DrawingVisual>でレンダリングされて<xref:System.Windows.Media.FormattedText>です。</span><span class="sxs-lookup"><span data-stu-id="e43d1-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="e43d1-105"><xref:System.Windows.Media.Visual>にレンダリングし、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>指定されたテキストのビットマップを作成します。</span><span class="sxs-lookup"><span data-stu-id="e43d1-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e43d1-106">例</span><span class="sxs-lookup"><span data-stu-id="e43d1-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="e43d1-107">参照</span><span class="sxs-lookup"><span data-stu-id="e43d1-107">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="e43d1-108">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="e43d1-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="e43d1-109">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="e43d1-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="e43d1-110">DrawingVisual オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="e43d1-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
