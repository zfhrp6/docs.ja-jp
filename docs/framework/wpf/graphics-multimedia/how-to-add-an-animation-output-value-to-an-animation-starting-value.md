---
title: "方法 : アニメーションの出力値をアニメーションの開始値に追加する | Microsoft Docs"
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
  - "アニメーション"
  - "IsAdditive プロパティ"
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : アニメーションの出力値をアニメーションの開始値に追加する
この例では、アニメーションの出力値をアニメーションの開始値に追加する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> プロパティは、アニメーションの出力値を、アニメーション化するプロパティの開始値 \(基本値\) に追加するかどうかを指定します。  <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> プロパティは、ほとんどの基本アニメーションとキー フレーム アプリケーションで使用できます。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」および「[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> で <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=fullName> プロパティを使用した場合の効果、および <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> で <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=fullName> プロパティを使用した場合の効果を次の例に示します。  
  
 [!code-xml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## 参照  
 [反復サイクル中にアニメーション値を累積する](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)