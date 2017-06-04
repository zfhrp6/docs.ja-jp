---
title: "方法 : 反復サイクル中にアニメーション値を累積する | Microsoft Docs"
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
  - "累積 (反復サイクル中にアニメーション値を)"
  - "アニメーション, 累積 (反復サイクル中に値を)"
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : 反復サイクル中にアニメーション値を累積する
この例では、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> プロパティを使用して、反復サイクル中にアニメーション値を累積する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> プロパティを使用して、反復サイクル中にアニメーションの基本値を累積します。  たとえば、アニメーションを 9 回反復 \(<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> \= "9x"\) するように設定し、10 から 15 までアニメーション化する \(From \= 10 To \= 15\) ようにプロパティを設定した場合、プロパティは、最初のサイクルでは 10 から 15 まで、2 回目のサイクルでは 15 から 20 まで、3 回目のサイクルでは 20 から 25 までというようにアニメーション化します。  つまり、前のアニメーション サイクルの終了値が、各アニメーション サイクルの基本値として使用されることになります。  
  
 `IsCumulative` プロパティは、ほとんどの基本アニメーションとキー フレーム アプリケーションで使用できます。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」および「[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)」を参照してください。  
  
 次の例では、4 つの四角形の幅をアニメーション化してこの動作を示します。  この例では、次の操作を実行します。  
  
-   <xref:System.Windows.Media.Animation.DoubleAnimation> で最初の四角形をアニメーション化し、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> プロパティを `true` に設定します。  
  
-   <xref:System.Windows.Media.Animation.DoubleAnimation> で 2 番目の四角形をアニメーション化し、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> プロパティを既定値の `false` に設定します。  
  
-   <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> で 3 番目の四角形をアニメーション化し、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> プロパティを `true` に設定します。  
  
-   <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> で最後の四角形をアニメーション化し、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> プロパティを `false` に設定します。  
  
 [!code-xml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## 参照  
 [アニメーションの出力値をアニメーションの開始値に追加する](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)   
 [アニメーションを反復する](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)