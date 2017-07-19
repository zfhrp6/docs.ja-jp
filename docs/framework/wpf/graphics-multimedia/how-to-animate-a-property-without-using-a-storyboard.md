---
title: "方法 : ストーリーボードを使用せずにプロパティをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 非ストーリーボード (ローカル)"
  - "ローカル アニメーション"
  - "非ストーリーボード アニメーション"
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : ストーリーボードを使用せずにプロパティをアニメーション化する
この例では、<xref:System.Windows.Media.Animation.Storyboard> を使用せずにアニメーションをプロパティに適用する方法を示します。  
  
> [!NOTE]
>  この機能は [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では使用できません。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でプロパティをアニメーション化する方法については、「[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)」を参照してください。  
  
 ローカル アニメーションをプロパティに適用するには、<xref:System.Windows.UIElement.BeginAnimation%2A> メソッドを使用します。  このメソッドは 2 つのパラメーターを受け取ります。1 つはアニメーション化するプロパティを指定する <xref:System.Windows.DependencyProperty> で、もう 1 つはプロパティに適用するアニメーションです。  
  
## 使用例  
 <xref:System.Windows.Controls.Button> の幅および背景色をアニメーション化する方法を次の例に示します。  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <xref:System.Windows.Media.Animation> 名前空間には、さまざまな種類のプロパティをアニメーション化するためのさまざまなアニメーション クラスがあります。  プロパティのアニメーション化の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  [依存関係プロパティ](GTMT) \(これらの例に示されているプロパティの種類\) とその機能の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用せずにアニメーション化する方法は他にもあります。詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.AnimationTimeline>   
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)