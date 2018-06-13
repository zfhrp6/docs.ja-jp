---
title: '方法 : ストーリーボードを使用せずにプロパティをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 18f8fb4edf5f71904335180e43dd65bd9910bdef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561015"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>方法 : ストーリーボードを使用せずにプロパティをアニメーション化する
この例を使用せず、プロパティにアニメーションを適用する方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>です。  
  
> [!NOTE]
>  この機能は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では使用できません。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でプロパティをアニメーション化する方法については、「[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)」を参照してください。  
  
 適用するには、ローカルのアニメーション プロパティを使用して、<xref:System.Windows.UIElement.BeginAnimation%2A>メソッドです。 このメソッドは、2 つのパラメーター: <xref:System.Windows.DependencyProperty> 、アニメーション化するプロパティとそのプロパティに適用するアニメーションを指定します。  
  
## <a name="example"></a>例  
 次の例の幅と背景色をアニメーション化する方法を示しています、<xref:System.Windows.Controls.Button>です。  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 アニメーションのクラスのさまざまな、<xref:System.Windows.Media.Animation>さまざまな種類のプロパティをアニメーション化する名前空間が存在します。 プロパティのアニメーション化の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。 依存関係プロパティ (これらの例に示されているプロパティの種類) とその機能の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
 使用せずにアニメーション化するには、その他の方法がある<xref:System.Windows.Media.Animation.Storyboard>オブジェクトです。 詳細については、次を参照してください。[プロパティ アニメーションの技術概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
