---
title: "方法: WDP イメージをエンコードおよびデコードする | Microsoft Docs"
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
  - "デコード (WDP イメージを)"
  - "エンコード (イメージ形式を)"
  - "エンコード (WDP イメージを)"
  - "WDP のデコード"
  - "WDP のエンコード"
ms.assetid: 911777d1-516b-49db-a87b-b54e31b18532
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法: WDP イメージをエンコードおよびデコードする
次の例では、特定の <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> オブジェクトと <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> オブジェクトを使用して、[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] イメージをデコードおよびエンコードする方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Uri> から <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> を使用して [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] イメージをデコードする方法を示します。  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Imaging.WmpBitmapEncoder> を使用して、<xref:System.Windows.Media.Imaging.BitmapSource> を [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] イメージにエンコードする方法を示します。  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## 参照  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)