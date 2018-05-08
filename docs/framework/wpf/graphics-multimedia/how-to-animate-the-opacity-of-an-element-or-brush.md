---
title: '方法 : 要素またはブラシの不透明度をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: a45bf0344c10e1214aa5218e25e9bd9a87d5ea60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>方法 : 要素またはブラシの不透明度をアニメーション化する
フレームワーク要素がフェードインおよびフェードアウトするために、アニメーション化できますその<xref:System.Windows.UIElement.Opacity%2A>またはプロパティをアニメーション化することができます、<xref:System.Windows.Media.Brush.Opacity%2A>のプロパティ、 <xref:System.Windows.Media.Brush> (またはブラシ) ペイントするために使用します。 でき、要素の不透明度をアニメーション化してその子のフェードインおよびフェードアウトが要素のどの部分がフェードインはより慎重に選択する要素の描画に使用するブラシをアニメーション化することができます。 たとえば、ボタンの背景の描画に使用されるブラシの不透明度をアニメーション化する可能性があります。 これにより、ビュー、そのテキストを完全に不透明なままのフェードインおよびフェードアウトするボタンの背景が原因です。  
  
> [!NOTE]
>  アニメーション化する、<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.Brush>アニメーションを超えるパフォーマンス上の利点を提供、<xref:System.Windows.UIElement.Opacity%2A>要素のプロパティです。  
  
 次の例では、2 つのボタンをアニメーション化してフェードインおよびフェードアウトします。 最初の不透明度<xref:System.Windows.Controls.Button>とアニメーション`1.0`に`0.0`経由で、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 秒間です。 、2 番目のボタンがアニメーション化もが描画に使用される、SolidColorBrush の不透明度その<xref:System.Windows.Controls.Control.Background%2A>全体のボタンの不透明度ではなくアニメーション化します。 この例を実行すると、最初のボタン完全にフェードインおよびフェードアウト、2 番目のボタンの背景のみがフェードインおよびフェードアウト中にします。 テキストと境界線は、完全に不透明のままになります。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 コードは、この例から省略されています。 完全なサンプルでは、不透明度をアニメーション化する方法も示しています、<xref:System.Windows.Media.Color>内で、<xref:System.Windows.Media.LinearGradientBrush>です。  サンプル全体については、次を参照してください。、[要素のサンプルの不透明度をアニメーション化](http://go.microsoft.com/fwlink/?LinkID=159968)です。
