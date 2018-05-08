---
title: '方法 : "From"、"To"、および "By" を使用してアニメーションを制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: c6f2bfb207163136d79e815e7f910673e8fafade
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>方法 : "From"、"To"、および "By" を使用してアニメーションを制御する
「から/に/される」または「基本的なアニメーション」が 2 つのターゲット値の間の遷移を作成 (を参照してください[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)アニメーションのさまざまな種類の概要について)。 基本的なアニメーションのターゲット値を設定するを使用してその<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。  次の表方法、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティは一緒に使用される可能性がありますまたは単独で、アニメーションのターゲットを決定する値します。  
  
|指定するプロパティ|結果として生じる動作|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティをアニメーション化されているプロパティのベース値または前のアニメーションの前のアニメーションの構成方法に応じて、値を出力します。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティで指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティの合計で指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|アニメーションがアニメーション化されたプロパティの基本値から移行するか、前のアニメーションの出力値を指定する値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|出力で指定された値とその値を合計する値をアニメーション化されているプロパティのベース値からアニメーション、または前のアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。|  
  
> [!NOTE]
>  両方を設定しないでください、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティおよび<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>同じアニメーションのプロパティです。  
  
 他の補間方式を使用したり、3 つ以上のターゲット値の間でアニメーション化したりするには、キー フレーム アニメーションを使用します。 参照してください[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)詳細についてはします。  
  
 1 つのプロパティを複数のアニメーションを適用する方法については、次を参照してください。[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。  
  
 次の例は、さまざまな設定の効果を示しています。 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションのプロパティです。  
  
## <a name="example"></a>例  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [アニメーションのターゲット値 (From、To、および By) のサンプル](http://go.microsoft.com/fwlink/?LinkID=159988)
