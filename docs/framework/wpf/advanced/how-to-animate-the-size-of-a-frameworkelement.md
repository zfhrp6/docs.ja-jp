---
title: '方法 : FrameworkElement のサイズをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: 148e3d592e129984bd2f7ac062340c5169e48d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543986"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>方法 : FrameworkElement のサイズをアニメーション化する
サイズをアニメーション化する、 <xref:System.Windows.FrameworkElement>、アニメーション化することができますか、その<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティまたはを使用して、アニメーション<xref:System.Windows.Media.ScaleTransform>です。  
  
 次の例では、これら 2 つの方法を使用して 2 つのボタンのサイズをアニメーション化します。 アニメーション化により 1 つのボタンがサイズ変更、<xref:System.Windows.FrameworkElement.Width%2A>プロパティと別のアニメーションでサイズを変更、<xref:System.Windows.Media.ScaleTransform>に適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。 各ボタンには、いくつかのテキストが含まれています。 最初に、両方のボタンで、同じテキストが表示されますが、2 番目のボタンのテキストになりますがゆがんで表示されるように、ボタンのサイズが変更されます。  
  
## <a name="example"></a>例  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 要素を変換する場合は、全体の要素とその内容が変換されます。 場合の最初のボタンのように、要素のサイズを直接変更するときに、そのサイズと位置がその親要素のサイズに依存しない限り、要素の内容はサイズ変更されません。  
  
 要素のサイズをアニメーション化するアニメーションの変換を適用することでその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティをアニメーションより優れたパフォーマンスを提供するその<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>を直接ため、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティでは、レイアウト パスは発生しません。  
  
 プロパティをアニメーション化の詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。 変換の詳細については、次を参照してください。、[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)です。
