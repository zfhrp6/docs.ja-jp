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
ms.openlocfilehash: 7aabb01d35e02323785b6bae0764a8d8bc636e16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>方法 : ビジュアルからビットマップを作成する
この例からビットマップを作成する方法、<xref:System.Windows.Media.Visual>です。 A<xref:System.Windows.Media.DrawingVisual>でレンダリングされて<xref:System.Windows.Media.FormattedText>です。 <xref:System.Windows.Media.Visual>にレンダリングし、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>指定されたテキストのビットマップを作成します。  
  
## <a name="example"></a>例  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.DrawingContext>  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
