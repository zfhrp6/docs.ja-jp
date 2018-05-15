---
title: '方法: GIF イメージをエンコードおよびデコードする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
ms.openlocfilehash: 9e432b5662843fe66cd8a8c445a3e4ec7c6d621b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="1d2cd-102">方法: GIF イメージをエンコードおよびデコードする</span><span class="sxs-lookup"><span data-stu-id="1d2cd-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="1d2cd-103">次の例は、デコードとエンコード方法を示して、 [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] 、固有の仕様を使用するイメージ<xref:System.Windows.Media.Imaging.GifBitmapDecoder>と<xref:System.Windows.Media.Imaging.GifBitmapEncoder>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1d2cd-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2cd-104">例</span><span class="sxs-lookup"><span data-stu-id="1d2cd-104">Example</span></span>  
 <span data-ttu-id="1d2cd-105">この例では、デコード、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.GifBitmapDecoder>から、<xref:System.IO.FileStream>です。</span><span class="sxs-lookup"><span data-stu-id="1d2cd-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="1d2cd-106">例</span><span class="sxs-lookup"><span data-stu-id="1d2cd-106">Example</span></span>  
 <span data-ttu-id="1d2cd-107">この例では、エンコード、<xref:System.Windows.Media.Imaging.BitmapSource>に、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.GifBitmapEncoder>です。</span><span class="sxs-lookup"><span data-stu-id="1d2cd-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1d2cd-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d2cd-108">See Also</span></span>  
 [<span data-ttu-id="1d2cd-109">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="1d2cd-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
