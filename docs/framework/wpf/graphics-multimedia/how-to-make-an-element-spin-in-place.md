---
title: "方法 : 要素のスピンを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e7dac2b1afb9d0ed385f3c25c2e30a93ea8a24f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
