---
title: "方法 : ビジュアルをイメージ ファイルにエンコードする"
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
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0a1ff9de1f5ddfdabbf7af7fef5f78046c14f8ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="9dd23-102">方法 : ビジュアルをイメージ ファイルにエンコードする</span><span class="sxs-lookup"><span data-stu-id="9dd23-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="9dd23-103">エンコードする方法を示します、<xref:System.Windows.Media.Visual>にイメージ ファイルを使用して、オブジェクト、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>と<xref:System.Windows.Media.Imaging.PngBitmapEncoder>です。</span><span class="sxs-lookup"><span data-stu-id="9dd23-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd23-104">例</span><span class="sxs-lookup"><span data-stu-id="9dd23-104">Example</span></span>  
 <span data-ttu-id="9dd23-105"><xref:System.Windows.Media.DrawingVisual>を使用して作成されて、<xref:System.Windows.Media.Imaging.BitmapImage>と<xref:System.Windows.Media.FormattedText>にレンダリングされる、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>です。</span><span class="sxs-lookup"><span data-stu-id="9dd23-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="9dd23-106">レンダリングされたビットマップを使用して、作成、<xref:System.Windows.Media.Imaging.BitmapFrame>に追加されます、<xref:System.Windows.Media.Imaging.PngBitmapEncoder>新しい[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]ファイル。</span><span class="sxs-lookup"><span data-stu-id="9dd23-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="9dd23-107">A<xref:System.Windows.Media.Imaging.PngBitmapEncoder>この例では、派生のいずれかで使用されていた<xref:System.Windows.Media.Imaging.BitmapEncoder>オブジェクトをイメージ ファイルの作成に使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9dd23-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd23-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dd23-108">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="9dd23-109">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="9dd23-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="9dd23-110">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="9dd23-110">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="9dd23-111">DrawingVisual オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="9dd23-111">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
