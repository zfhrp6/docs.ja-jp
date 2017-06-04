---
title: "方法 : ビジュアルをイメージ ファイルにエンコードする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エンコード (イメージ形式を)"
  - "イメージ ファイル, エンコード (ビジュアルから)"
  - "ビジュアル, エンコード (イメージ ファイルに)"
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : ビジュアルをイメージ ファイルにエンコードする
この例では、<xref:System.Windows.Media.Imaging.RenderTargetBitmap> と <xref:System.Windows.Media.Imaging.PngBitmapEncoder> を使用して <xref:System.Windows.Media.Visual> オブジェクトをイメージ ファイルにエンコードする方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Imaging.BitmapImage> と <xref:System.Windows.Media.FormattedText> を使用して <xref:System.Windows.Media.DrawingVisual> を作成し、<xref:System.Windows.Media.Imaging.RenderTargetBitmap> にレンダリングします。  次に、レンダリングしたビットマップを使用して <xref:System.Windows.Media.Imaging.BitmapFrame> を作成し、それを <xref:System.Windows.Media.Imaging.PngBitmapEncoder> に追加して新しい[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] ファイルを作成します。  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 この例では <xref:System.Windows.Media.Imaging.PngBitmapEncoder> を使用しましたが、<xref:System.Windows.Media.Imaging.BitmapEncoder> から派生した任意のオブジェクトを使用して、イメージ ファイルを作成できます。  
  
## 参照  
 <xref:System.Windows.Media.DrawingContext>   
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)