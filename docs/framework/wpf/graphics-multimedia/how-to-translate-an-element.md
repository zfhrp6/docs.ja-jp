---
title: "方法 : 要素を変換する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 222aebe0ffe3d2bb1d84002a2ad94b0b92ede15b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-translate-an-element"></a>方法 : 要素を変換する
この例では変換 (移動) 要素を使用して、<xref:System.Windows.Media.TranslateTransform>です。  
  
 <xref:System.Windows.Media.TranslateTransform>クラスは、絶対位置指定をサポートしていないパネル内の要素を移動するために特に便利です。 適用することで、たとえば、<xref:System.Windows.Media.TranslateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティ内の要素を移動することができます、<xref:System.Windows.Controls.StackPanel>または<xref:System.Windows.Controls.DockPanel>です。  
  
 使用して、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> (ピクセル単位) を x 軸に要素を移動する量を指定します。 使用して、<xref:System.Windows.Media.TranslateTransform.Y%2A>プロパティ (ピクセル単位) を y 軸に沿った要素を移動する量を指定します。 最後に、適用、<xref:System.Windows.Media.TranslateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティです。  
  
 次の例では、<xref:System.Windows.Media.TranslateTransform>下に移動する要素を 50 ピクセルを左右に 50 ピクセルです。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
