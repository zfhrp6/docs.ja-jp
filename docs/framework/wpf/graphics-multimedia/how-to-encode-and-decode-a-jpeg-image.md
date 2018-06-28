---
title: '方法: エンコードおよびデコード JPEG イメージ'
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
ms.openlocfilehash: 916eab63938100daf91e6c1a5af31648a99108d0
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027968"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="4a95a-102">方法: エンコードおよびデコード JPEG イメージ</span><span class="sxs-lookup"><span data-stu-id="4a95a-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="4a95a-103">次の例は、デコードし、固有の仕様を使用して、JPEG イメージのエンコード方法を示して<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>と<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4a95a-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="4a95a-104">例 - JPEG イメージ デコード</span><span class="sxs-lookup"><span data-stu-id="4a95a-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="4a95a-105">この例では、JPEG 画像を使用して、デコード、<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>から、<xref:System.IO.FileStream>です。</span><span class="sxs-lookup"><span data-stu-id="4a95a-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="4a95a-106">例 - エンコード JPEG イメージ</span><span class="sxs-lookup"><span data-stu-id="4a95a-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="4a95a-107">この例では、エンコード、 <xref:System.Windows.Media.Imaging.BitmapSource> JPEG にイメージを使用して、<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>です。</span><span class="sxs-lookup"><span data-stu-id="4a95a-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4a95a-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a95a-108">See also</span></span>

[<span data-ttu-id="4a95a-109">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="4a95a-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)