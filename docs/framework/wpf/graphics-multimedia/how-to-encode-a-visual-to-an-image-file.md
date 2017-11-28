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
# <a name="how-to-encode-a-visual-to-an-image-file"></a>方法 : ビジュアルをイメージ ファイルにエンコードする
エンコードする方法を示します、<xref:System.Windows.Media.Visual>にイメージ ファイルを使用して、オブジェクト、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>と<xref:System.Windows.Media.Imaging.PngBitmapEncoder>です。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.DrawingVisual>を使用して作成されて、<xref:System.Windows.Media.Imaging.BitmapImage>と<xref:System.Windows.Media.FormattedText>にレンダリングされる、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>です。 レンダリングされたビットマップを使用して、作成、<xref:System.Windows.Media.Imaging.BitmapFrame>に追加されます、<xref:System.Windows.Media.Imaging.PngBitmapEncoder>新しい[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]ファイル。  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 A<xref:System.Windows.Media.Imaging.PngBitmapEncoder>この例では、派生のいずれかで使用されていた<xref:System.Windows.Media.Imaging.BitmapEncoder>オブジェクトをイメージ ファイルの作成に使用する可能性があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.DrawingContext>  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
