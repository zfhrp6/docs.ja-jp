---
title: "方法 : アニメーションを反復する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アニメーション, 繰り返し"
  - "RepeatBehavior プロパティ (タイムラインの)"
  - "反復 (アニメーションを)"
  - "タイムラインの RepeatBehavior プロパティ"
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : アニメーションを反復する
アニメーションの繰り返し動作を制御するために <xref:System.Windows.Media.Animation.Timeline> の <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> プロパティを使用する方法を次の例に示します。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.Timeline> コントロールの <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> プロパティは、アニメーションが単純継続時間を繰り返す回数を制御します。  <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> を使用して、<xref:System.Windows.Media.Animation.Timeline> が特定の回数 \(反復カウント\) または指定した期間、繰り返すことを指定できます。  いずれの場合も、アニメーションは、要求されたカウントまたは期間を満たすのに必要な回数だけ実行を繰り返します。  
  
 既定では、タイムラインの反復カウントは 1.0 です。これは、再生回数が 1 回で、繰り返されないことを意味します。  ただし、<xref:System.Windows.Media.Animation.Timeline> の <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> プロパティを <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A> に設定した場合、タイムラインは無限に繰り返します。  
  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> プロパティを使用してアニメーションの繰り返し動作を制御する方法を次の例に示します。  この例は、それぞれの四角形で異なる種類の繰り返し動作を使用する 5 つの四角形の <xref:System.Windows.FrameworkElement.Width%2A> プロパティをアニメーション化しています。  
  
 [!code-xml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 サンプル全体については、[アニメーションのタイミング動作のサンプル](http://go.microsoft.com/fwlink/?LinkID=159970)を参照してください。  
  
## 参照  
 [反復サイクル中にアニメーション値を累積する](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)   
 [タイムラインを自動的に反転するかどうかを指定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [アニメーションのタイミング動作のサンプル](http://go.microsoft.com/fwlink/?LinkID=159970)