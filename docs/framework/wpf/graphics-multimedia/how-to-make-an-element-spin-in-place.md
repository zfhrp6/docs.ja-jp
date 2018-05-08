---
title: '方法 : 要素のスピンを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a37952af621c79d231b45a247c92d3576a533580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-an-element-spin-in-place"></a>方法 : 要素のスピンを設定する
この例は、スピンを使用して要素を作成する方法を示しています、<xref:System.Windows.Media.RotateTransform>と<xref:System.Windows.Media.Animation.DoubleAnimation>です。  
  
 次の例に適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティです。 この例では、<xref:System.Windows.Media.Animation.DoubleAnimation>アニメーション化する、<xref:System.Windows.Media.RotateTransform.Angle%2A>の<xref:System.Windows.Media.RotateTransform>です。 例を設定するのには、要素を回転、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>点 (0.5, 0.5) する要素のプロパティです。  
  
## <a name="example"></a>例  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 例については変換が含まれている完全なサンプルは、次を参照してください。 [2-d 変換サンプル](http://go.microsoft.com/fwlink/?LinkID=158252)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
