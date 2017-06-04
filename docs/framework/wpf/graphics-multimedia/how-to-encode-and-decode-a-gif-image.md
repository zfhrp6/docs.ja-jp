---
title: "方法: GIF イメージをエンコードおよびデコードする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デコード (GIF イメージを)"
  - "デコード (イメージ形式を)"
  - "エンコード (GIF イメージを)"
  - "エンコード (イメージ形式を)"
  - "GIF のデコード"
  - "GIF のエンコード"
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法: GIF イメージをエンコードおよびデコードする
次の例では、特定の <xref:System.Windows.Media.Imaging.GifBitmapDecoder> オブジェクトと <xref:System.Windows.Media.Imaging.GifBitmapEncoder> オブジェクトを使用して、[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] イメージをデコードおよびエンコードする方法を示します。  
  
## 使用例  
 次の例では、<xref:System.IO.FileStream> から <xref:System.Windows.Media.Imaging.GifBitmapDecoder> を使用して [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] イメージをデコードする方法を示します。  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Imaging.GifBitmapEncoder> を使用して、<xref:System.Windows.Media.Imaging.BitmapSource> を [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] イメージにエンコードする方法を示します。  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## 参照  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)