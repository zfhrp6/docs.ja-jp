---
title: "方法: GIF イメージをエンコードおよびデコードする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7832e4197ef5c3a764da265a393b654db013876
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="9bdbb-102">方法: GIF イメージをエンコードおよびデコードする</span><span class="sxs-lookup"><span data-stu-id="9bdbb-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="9bdbb-103">次の例は、デコードとエンコード方法を示して、 [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] 、固有の仕様を使用するイメージ<xref:System.Windows.Media.Imaging.GifBitmapDecoder>と<xref:System.Windows.Media.Imaging.GifBitmapEncoder>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9bdbb-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bdbb-104">例</span><span class="sxs-lookup"><span data-stu-id="9bdbb-104">Example</span></span>  
 <span data-ttu-id="9bdbb-105">この例では、デコード、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.GifBitmapDecoder>から、<xref:System.IO.FileStream>です。</span><span class="sxs-lookup"><span data-stu-id="9bdbb-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9bdbb-106">例</span><span class="sxs-lookup"><span data-stu-id="9bdbb-106">Example</span></span>  
 <span data-ttu-id="9bdbb-107">この例では、エンコード、<xref:System.Windows.Media.Imaging.BitmapSource>に、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]を使用するイメージ、<xref:System.Windows.Media.Imaging.GifBitmapEncoder>です。</span><span class="sxs-lookup"><span data-stu-id="9bdbb-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9bdbb-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bdbb-108">See Also</span></span>  
 [<span data-ttu-id="9bdbb-109">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="9bdbb-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
