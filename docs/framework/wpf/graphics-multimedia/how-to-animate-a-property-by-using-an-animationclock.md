---
title: "方法 : AnimationClock を使用してプロパティをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, プロパティ, AnimationClock を使用"
  - "AnimationClock"
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : AnimationClock を使用してプロパティをアニメーション化する
この例では、<xref:System.Windows.Media.Animation.Clock> オブジェクトを使用してプロパティをアニメーション化する方法を説明します。  
  
 [依存関係プロパティ](GTMT)をアニメーション化するには次の 3 つの方法があります。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline> を作成し、<xref:System.Windows.Media.Animation.Storyboard> を使用してアニメーション化するプロパティに関連付ける。  
  
-   オブジェクトの <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用して、1 つの <xref:System.Windows.Media.Animation.AnimationTimeline> をターゲット プロパティに適用する。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline> から <xref:System.Windows.Media.Animation.AnimationClock> を作成してプロパティに適用する。  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトおよび <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用すると、クロックを直接作成または配布しなくても、プロパティをアニメーション化できます \(例については、「[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)」および「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください\)。つまり、クロックは自動的に作成および配布されます。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.AnimationClock> を作成し、2 つの類似するプロパティにこれを適用する方法を次の例に示します。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <xref:System.Windows.Media.Animation.Clock> の開始後にこれを対話的に制御する方法の例については、「[クロックを対話的に制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)」を参照してください。  
  
## 参照  
 [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)