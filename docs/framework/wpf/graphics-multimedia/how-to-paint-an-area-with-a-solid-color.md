---
title: "方法 : 純色で領域を塗りつぶす"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a5fe948c3cc6088f238f1f8f53c26c5f1fa5b2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>方法 : 純色で領域を塗りつぶす
純色で領域を塗りつぶす、する定義済みのシステム ブラシなど、使用できる<xref:System.Windows.Media.Brushes.Red%2A>または<xref:System.Windows.Media.Brushes.Blue%2A>、または新規に作成することができます<xref:System.Windows.Media.SolidColorBrush>について説明し、<xref:System.Windows.Media.SolidColorBrush.Color%2A>アルファ、赤、緑、および青の値を使用します。 XAML では、16 進数表記を使用して、純色で領域を塗りつぶすこともできます。  
  
 次の例を使用してこれらの方法を描画する、<xref:System.Windows.Shapes.Rectangle>青。  
  
## <a name="example"></a>例  
 **定義済みのブラシの使用**  
  
 次の例では、定義済みのブラシを使用して<xref:System.Windows.Media.Brushes.Blue%2A>青い四角形を描画します。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **16 進数表記の使用**  
  
 次の例では、8 桁の 16 進数表記を使用して、四角形を青で塗りつぶします。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB 値の使用**  
  
 次の例では、作成、<xref:System.Windows.Media.SolidColorBrush>について説明し、 <xref:System.Windows.Media.SolidColorBrush.Color%2A> ARGB を使用して、色の青の値します。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 他の色を記述する方法についてを参照してください。、<xref:System.Windows.Media.Color>構造体。  
  
 **関連トピック**  
  
 詳細については<xref:System.Windows.Media.SolidColorBrush>し、その他の例を参照してください、[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)の概要です。  
  
 このコード例に示されている例の一部である、<xref:System.Windows.Media.SolidColorBrush>クラスです。 完全なサンプルについては、「[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Brushes>
