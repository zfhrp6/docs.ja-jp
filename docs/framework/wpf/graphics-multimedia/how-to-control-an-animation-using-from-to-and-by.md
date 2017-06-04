---
title: "方法 : &quot;From&quot;、&quot;To&quot;、および &quot;By&quot; を使用してアニメーションを制御する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アニメーションによって/"
  - "基本アニメーション"
  - "アニメーション、基本アニメーション"
  - "From/To/By アニメーション"
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : &quot;From&quot;、&quot;To&quot;、および &quot;By&quot; を使用してアニメーションを制御する
「から/に/者」または「基本アニメーション」が&2; つのターゲット値の間の遷移を作成 (を参照してください[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)さまざまな種類のアニメーションの概要について)。 基本的なアニメーションのターゲット値を設定するには、使用、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。  次の表方法<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティを併用することがありますかとは別に、アニメーションのターゲットを決定する値します。  
  
|指定されたプロパティ|結果の動作|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティをアニメーション化するプロパティの基本値または前のアニメーションの前のアニメーションの構成方法に応じて、値を出力します。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and                              <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティで指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and                              <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティの合計で指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|アニメーションがアニメーション化されたプロパティの基本値から移行するか、前のアニメーションの出力値を指定する値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|出力にその値と指定する値の合計値をアニメーションをアニメーション化するプロパティの基本値または前のアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。|  
  
> [!NOTE]
>  両方を設定しないで、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティおよび<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>同じアニメーションのプロパティです。  
  
 その他の補間方法を使用する&3; つ以上のターゲット値の間をアニメーション化するには、キー フレーム アニメーションを使用します。 参照してください[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)の詳細。  
  
 1 つのプロパティに複数のアニメーションを適用する方法については、次を参照してください。[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)します。  
  
 次の例は、さまざまな設定の効果を示しています。<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションのプロパティです。  
  
## <a name="example"></a>例  
 [!code-xml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [From、To、およびアニメーションのターゲット値のサンプルで](http://go.microsoft.com/fwlink/?LinkID=159988)