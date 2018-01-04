---
title: "方法 : 放射状グラデーションを使用して領域を塗りつぶす"
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
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1da933a2ee7c179a55da7d33c61539d440eabc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>方法 : 放射状グラデーションを使用して領域を塗りつぶす
この例を使用する方法を示しています、<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーションで領域を塗りつぶすクラス。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーション赤青の淡い緑から黄色から遷移を含む四角形を描画します。  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 次の図は、前の例からのグラデーションを示します。 グラデーションの終了位置が示されています。  
  
 ![放射状グラデーションでのグラデーション境界](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  このトピックの例では、制御点を設定するための既定の座標系を使用します。 既定の座標システムは境界ボックスに対する相対: 0%、境界ボックスの場合は 0、1 は、境界ボックスの 100% を示します。 この座標系を変更するには設定して、<xref:System.Windows.Media.GradientBrush.MappingMode%2A>プロパティ値を<xref:System.Windows.Media.BrushMappingMode.Absolute>です。 絶対座標系は、境界ボックスに相対しません。 値は、ローカル空間に直接変換されます。  
  
 追加<xref:System.Windows.Media.RadialGradientBrush>例についてを参照してください、[ブラシ サンプル](http://go.microsoft.com/fwlink/?LinkID=159973)です。 グラデーションおよびその他の種類のブラシの詳細については、次を参照してください。[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。
