---
title: '方法: JPEG イメージをエンコードおよびデコードする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
ms.openlocfilehash: 8eb3c2573ba23fa62550e7e60489b13a37eb7cc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a>方法: JPEG イメージをエンコードおよびデコードする
次の例は、デコードとエンコード方法を示して、 [!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)] 、固有の仕様を使用するイメージ<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>と<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>オブジェクト。  
  
## <a name="example"></a>例  
 この例では、デコード、[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>から、<xref:System.IO.FileStream>です。  
  
 [!code-cpp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
 [!code-csharp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
 [!code-vb[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example"></a>例  
 この例では、エンコード、<xref:System.Windows.Media.Imaging.BitmapSource>に、[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>です。  
  
 [!code-cpp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
 [!code-csharp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
 [!code-vb[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
  
## <a name="see-also"></a>関連項目  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
