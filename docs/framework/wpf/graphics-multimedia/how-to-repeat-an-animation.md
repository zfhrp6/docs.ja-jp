---
title: "方法 : アニメーションを反復する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2f942771e01c2b7fae989f73779672edb8ba2f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-repeat-an-animation"></a>方法 : アニメーションを反復する
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>アニメーションの繰り返し動作を制御するためにします。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>アニメーションが一定時間の再生を繰り返す回数を制御します。 使用して<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>を指定することができます、<xref:System.Windows.Media.Animation.Timeline>回数だけ繰り返されます (反復カウント) か、指定された期間。 いずれの場合は、アニメーションは、要求されたカウントまたは期間を入力するために必要な数だけの先頭、末尾実行を通過します。  
  
 既定では、タイムラインは 1.0 では、これは、1 回だけ再生繰り返さないでの繰り返し回数があります。 ただし、設定した場合、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>に<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>タイムラインを無限に繰り返します。  
  
 次の例を使用する方法を示しています、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>アニメーションの繰り返し動作を制御するプロパティです。 例では、アニメーション、<xref:System.Windows.FrameworkElement.Width%2A>さまざまな種類の繰り返し動作を使用して各四角形で 5 つの四角形のプロパティです。  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 サンプル全体については、次を参照してください。[アニメーション タイミング動作サンプル](http://go.microsoft.com/fwlink/?LinkID=159970)です。  
  
## <a name="see-also"></a>関連項目  
 [反復サイクル中にアニメーション値を累積する](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [タイムラインを自動的に反転するかどうかを指定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [アニメーションおよびタイミング](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [アニメーションのタイミング動作のサンプル](http://go.microsoft.com/fwlink/?LinkID=159970)
