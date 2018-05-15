---
title: '方法: BMP イメージをエンコードおよびデコードする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
ms.openlocfilehash: d8815a6f52a4033ec2d7dc19b0f97c5e65f1e2b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a><span data-ttu-id="612aa-102">方法: BMP イメージをエンコードおよびデコードする</span><span class="sxs-lookup"><span data-stu-id="612aa-102">How to: Encode and Decode a BMP Image</span></span>
<span data-ttu-id="612aa-103">次の例は、デコードとエンコード方法を示して、 [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] 、固有の仕様を使用するイメージ<xref:System.Windows.Media.Imaging.BmpBitmapDecoder>と<xref:System.Windows.Media.Imaging.BmpBitmapEncoder>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="612aa-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] image using the specific <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="612aa-104">例</span><span class="sxs-lookup"><span data-stu-id="612aa-104">Example</span></span>  
 <span data-ttu-id="612aa-105">この例では、デコード、[!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.BmpBitmapDecoder>から、<xref:System.Uri>です。</span><span class="sxs-lookup"><span data-stu-id="612aa-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="612aa-106">例</span><span class="sxs-lookup"><span data-stu-id="612aa-106">Example</span></span>  
 <span data-ttu-id="612aa-107">この例では、エンコード、<xref:System.Windows.Media.Imaging.BitmapSource>に、[!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.BmpBitmapEncoder>です。</span><span class="sxs-lookup"><span data-stu-id="612aa-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="612aa-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="612aa-108">See Also</span></span>  
 [<span data-ttu-id="612aa-109">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="612aa-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
