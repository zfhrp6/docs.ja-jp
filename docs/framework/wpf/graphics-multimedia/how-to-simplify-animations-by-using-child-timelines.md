---
title: "方法 : 子タイムラインを使用してアニメーションを簡素化する | Microsoft Docs"
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
  - "アニメーション, 簡素化 (子タイムラインによる)"
  - "子タイムライン"
  - "簡素化 (子タイムラインを使用してアニメーションを)"
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 子タイムラインを使用してアニメーションを簡素化する
この例では、子 <xref:System.Windows.Media.Animation.ParallelTimeline> オブジェクトを使用してアニメーションを簡素化する方法を示します。  <xref:System.Windows.Media.Animation.Storyboard> は <xref:System.Windows.Media.Animation.Timeline> の型で、含まれる複数のタイムラインの対象情報を持っています。  <xref:System.Windows.Media.Animation.Storyboard> を使用して、オブジェクトおよびプロパティの情報を含むタイムラインの対象情報を提供します。  
  
 アニメーションを開始するには、1 つ以上の <xref:System.Windows.Media.Animation.ParallelTimeline> オブジェクトを、<xref:System.Windows.Media.Animation.Storyboard> の子要素として入れ子にして使用します。  この <xref:System.Windows.Media.Animation.ParallelTimeline> オブジェクトには、他のアニメーションを格納できるので、複雑なアニメーションのタイミング シーケンスを容易にカプセル化できます。  たとえば、1 つの <xref:System.Windows.Controls.TextBlock> といくつかの図形を同じ <xref:System.Windows.Media.Animation.Storyboard> 内でアニメーション化する場合に、<xref:System.Windows.Controls.TextBlock> のアニメーションと図形のアニメーションとを分離するには、それぞれを別の <xref:System.Windows.Media.Animation.ParallelTimeline> に配置します。  それぞれの <xref:System.Windows.Media.Animation.ParallelTimeline> には独自の <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> があり、<xref:System.Windows.Media.Animation.ParallelTimeline> のすべての子要素は、この <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> を基準として開始されるため、タイミングがより効率的にカプセル化されます。  
  
 この例では、2 つのテキスト \(<xref:System.Windows.Controls.TextBlock> オブジェクト\) を同じ <xref:System.Windows.Media.Animation.Storyboard> 内からアニメーション化します。  <xref:System.Windows.Media.Animation.ParallelTimeline> は、1 つの<xref:System.Windows.Controls.TextBlock> オブジェクトのアニメーションをカプセル化します。  
  
 **パフォーマンスに関するメモ :** <xref:System.Windows.Media.Animation.Storyboard> タイムラインどうしを入れ子にすることもできますが、入れ子にするには、オーバーヘッドの少ない <xref:System.Windows.Media.Animation.ParallelTimeline> の方が適しています   \(<xref:System.Windows.Media.Animation.Storyboard> クラスは <xref:System.Windows.Media.Animation.ParallelTimeline> クラスから継承されます\)。  
  
## 使用例  
 [!code-xml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボード アニメーション間で HandoffBehavior を指定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)