---
title: "方法: BMP イメージをエンコードおよびデコードする | Microsoft Docs"
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
  - "BMP のデコード"
  - "BMP のエンコード"
  - "デコード (BMP イメージを)"
  - "デコード (イメージ形式を)"
  - "エンコード (BMP イメージを)"
  - "エンコード (イメージ形式を)"
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法: BMP イメージをエンコードおよびデコードする
次の例では、特定の <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> オブジェクトと <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> オブジェクトを使用して、[!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] イメージをデコードおよびエンコードする方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Uri> から <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> を使用して [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] イメージをデコードする方法を示します。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Imaging.BmpBitmapEncoder> を使用して、<xref:System.Windows.Media.Imaging.BitmapSource> を [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] イメージにエンコードする方法を示します。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## 参照  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)