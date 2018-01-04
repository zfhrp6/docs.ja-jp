---
title: "方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2c1d65ec9fad94fed02bee1f018ae1aa00a8591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する
この例を指定する方法を示しています、 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 、非アクティブの<xref:System.Windows.Media.Animation.Timeline>アニメーション化されたプロパティのです。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>されていないときにアニメーション化されたプロパティの値に動作が決定されます、アニメーション化は、ときに、<xref:System.Windows.Media.Animation.Timeline>がその親がアクティブでない<xref:System.Windows.Media.Animation.Timeline>アクティブまたは保留期間。 たとえばはアニメーション化されたプロパティのまま、最後に、アニメーションを終了またはその後の値がアニメーションの開始前に、の値に戻すか。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>アニメーション化する、 <xref:System.Windows.FrameworkElement.Width%2A> 2 つの四角形。 各四角形を使用して、異なる<xref:System.Windows.Media.Animation.Timeline>オブジェクト。  
  
 1 つ<xref:System.Windows.Media.Animation.Timeline>が、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.Stop>、そのアニメーション化されていないに戻すに四角形の幅を停止するときの値、<xref:System.Windows.Media.Animation.Timeline>を終了します。 他の<xref:System.Windows.Media.Animation.Timeline>が、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>、それが原因で、幅の末尾にしたままにするときの値、<xref:System.Windows.Media.Animation.Timeline>を終了します。  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 サンプル全体については、次を参照してください。[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [アニメーションおよびタイミング](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
