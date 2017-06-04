---
title: "方法: PNG イメージをエンコードおよびデコードする | Microsoft Docs"
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
  - "デコード (PNG イメージを)"
  - "エンコード (イメージ形式を)"
  - "エンコード (PNG イメージを)"
  - "PNG のデコード"
  - "PNG のエンコード"
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法: PNG イメージをエンコードおよびデコードする
次の例では、特定の <xref:System.Windows.Media.Imaging.PngBitmapDecoder> オブジェクトと <xref:System.Windows.Media.Imaging.PngBitmapEncoder> オブジェクトを使用して、[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] イメージをデコードおよびエンコードする方法を示します。  
  
## 使用例  
 次の例では、<xref:System.IO.FileStream> から <xref:System.Windows.Media.Imaging.PngBitmapDecoder> を使用して [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] イメージをデコードする方法を示します。  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Imaging.PngBitmapEncoder> を使用して、<xref:System.Windows.Media.Imaging.BitmapSource> を [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] イメージにエンコードする方法を示します。  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## 参照  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)