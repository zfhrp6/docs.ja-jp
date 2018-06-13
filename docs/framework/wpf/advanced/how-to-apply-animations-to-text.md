---
title: '方法 : アニメーションをテキストに適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545439"
---
# <a name="how-to-apply-animations-to-text"></a>方法 : アニメーションをテキストに適用する
アニメーションを利用すると、アプリケーションのテキストの表示方法や見た目を変えることができます。 次の例では、アニメーションの別の種類を使用して、内のテキストの表示には影響を<xref:System.Windows.Controls.TextBlock>コントロール。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>テキスト ブロックの幅をアニメーション化します。 幅の値が 10 秒間、テキスト ブロックの幅から 0 に変化します。その後、幅の値を戻します。 この種類のアニメーションでワイプ効果を作ります。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>テキスト ブロックの不透明度をアニメーション化します。 不透明度の値が 5 秒間、1.0 から 0 に変化し、その後、不透明度の値を戻します。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 次の図の効果を示しています、<xref:System.Windows.Controls.TextBlock>コントロールからの不透明度を変更する`1.00`に`0.00`によって定義された 5 秒間隔の間に、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>です。  
  
 ![テキストの不透明度を 1.00 から 0.00 に変更する](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
テキストの不透明度が 1.00 から 0.00 に変化します  
  
 次の例では、<xref:System.Windows.Media.Animation.ColorAnimation>テキスト ブロックの前景色をアニメーション化します。 前景色の値が 5 秒間、ある色から別の色に変化し、その後、色の値を戻します。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>テキスト ブロックを回転します。 テキスト ブロックは 20 秒間、完全な回転を行い、その後、回転を引き続き繰り返します。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
