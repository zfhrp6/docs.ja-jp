---
title: "方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する | Microsoft Docs"
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
  - "FillBehavior プロパティ (アクティブでないタイムラインの)"
  - "タイムライン, FillBehavior プロパティ"
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する
この例では、アニメーション化されたプロパティのアクティブでない <xref:System.Windows.Media.Animation.Timeline> に対して <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> を指定する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.Timeline> の <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティは、アニメーション化されたプロパティがアニメーション化されていない場合、つまり <xref:System.Windows.Media.Animation.Timeline> はアクティブではないが、その親 <xref:System.Windows.Media.Animation.Timeline> はアクティブ期間または保留期間内にある場合に、そのプロパティの値の処理方法を決定します。  たとえば、アニメーション化されたプロパティが、アニメーションの終了後に、終了値の状態を維持するのか、アニメーションが開始される前の値に戻るのかを決定します。  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> を使用して、2 つの四角形の <xref:System.Windows.FrameworkElement.Width%2A> をアニメーション化する例を次に示します。  各四角形には、それぞれ別の <xref:System.Windows.Media.Animation.Timeline> オブジェクトを使用します。  
  
 一方の <xref:System.Windows.Media.Animation.Timeline> では、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> が <xref:System.Windows.Media.Animation.FillBehavior> に設定されているため、<xref:System.Windows.Media.Animation.Timeline> が終了すると、四角形の幅はアニメーション化される前の値に戻ります。  もう一方の <xref:System.Windows.Media.Animation.Timeline> では、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> が <xref:System.Windows.Media.Animation.FillBehavior> に設定されているため、<xref:System.Windows.Media.Animation.Timeline> が終了すると、幅は終了値の状態を維持します。  
  
 [!code-xml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 サンプル全体については、[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.DoubleAnimation>   
 <xref:System.Windows.FrameworkElement.Width%2A>   
 <xref:System.Windows.Media.Animation.Timeline>   
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>   
 <xref:System.Windows.Media.Animation.FillBehavior>   
 <xref:System.Windows.Media.Animation.FillBehavior>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)