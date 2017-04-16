---
title: "方法 : ビジュアルからビットマップを作成する | Microsoft Docs"
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
  - "ビットマップ, 描画 (ビジュアルから)"
  - "ビジュアル, レンダリング (ビットマップに)"
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : ビジュアルからビットマップを作成する
この例では、<xref:System.Windows.Media.Visual> からビットマップを作成する方法を示します。  <xref:System.Windows.Media.DrawingVisual> を <xref:System.Windows.Media.FormattedText> でレンダリングします。  次に、<xref:System.Windows.Media.Visual> を <xref:System.Windows.Media.Imaging.RenderTargetBitmap> にレンダリングして、指定したテキストのビットマップを作成します。  
  
## 使用例  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## 参照  
 <xref:System.Windows.Media.DrawingContext>   
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)