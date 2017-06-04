---
title: "方法: JPEG イメージをエンコードおよびデコードする | Microsoft Docs"
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
  - "デコード (イメージ形式を)"
  - "デコード (JPEG イメージを)"
  - "エンコード (イメージ形式を)"
  - "エンコード (JPEG イメージを)"
  - "JPEG のデコード"
  - "JPEG のエンコード"
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法: JPEG イメージをエンコードおよびデコードする
次の例では、特定の <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> オブジェクトと <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> オブジェクトを使用して、[!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)] イメージをデコードおよびエンコードする方法を示します。  
  
## 使用例  
 次の例では、<xref:System.IO.FileStream> から <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> を使用して [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] イメージをデコードする方法を示します。  
  
 [!code-cpp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
 [!code-csharp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
 [!code-vb[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Imaging.JpegBitmapEncoder> を使用して、<xref:System.Windows.Media.Imaging.BitmapSource> を [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] イメージにエンコードする方法を示します。  
  
 [!code-cpp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
 [!code-csharp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
 [!code-vb[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## .NET Framework セキュリティ  
  
## 参照  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)