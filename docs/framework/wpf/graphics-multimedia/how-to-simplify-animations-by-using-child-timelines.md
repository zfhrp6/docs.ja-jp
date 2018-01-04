---
title: "方法 : 子タイムラインを使用してアニメーションを簡素化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d3b8f1ca1dbf7ba5452acffc62fdf0b655c9c12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>方法 : 子タイムラインを使用してアニメーションを簡素化する
この例は、子を使用して、アニメーションを簡略化する方法を示しています。<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクト。 A<xref:System.Windows.Media.Animation.Storyboard>の種類は、<xref:System.Windows.Media.Animation.Timeline>が含まれているタイムラインの対象とする情報を提供します。 使用して、<xref:System.Windows.Media.Animation.Storyboard>オブジェクトとプロパティの情報などの情報を対象とするタイムラインを提供します。  
  
 アニメーションを開始するには、1 つまたは複数を使用して<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクトの入れ子になった子要素として、<xref:System.Windows.Media.Animation.Storyboard>です。 これら<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクトが他のアニメーションを含めることができ、そのためよりをカプセル化できる複雑なアニメーションのタイミング シーケンス。 アニメーションする場合など、<xref:System.Windows.Controls.TextBlock>と同じいくつかの図形<xref:System.Windows.Media.Animation.Storyboard>のアニメーションを分離することができます、<xref:System.Windows.Controls.TextBlock>とそれぞれ個別に配置すること、図形<xref:System.Windows.Media.Animation.ParallelTimeline>です。 各<xref:System.Windows.Media.Animation.ParallelTimeline>で独自<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>とのすべての子要素、<xref:System.Windows.Media.Animation.ParallelTimeline>基準としたこの開始<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>タイミングより適切にカプセル化します。  
  
 次の例では、2 つのテキスト (<xref:System.Windows.Controls.TextBlock>オブジェクト) から同じ<xref:System.Windows.Media.Animation.Storyboard>です。 A<xref:System.Windows.Media.Animation.ParallelTimeline>のいずれかのアニメーションをカプセル化、<xref:System.Windows.Controls.TextBlock>オブジェクト。  
  
 **パフォーマンスに関するメモ:**入れ子にすることが<xref:System.Windows.Media.Animation.Storyboard>、互いに内部タイムライン<xref:System.Windows.Media.Animation.ParallelTimeline>s はオーバーヘッドが少なくて済みますが要求されるために入れ子に適してします。 (、<xref:System.Windows.Media.Animation.Storyboard>クラスから継承、<xref:System.Windows.Media.Animation.ParallelTimeline>クラスです)。  
  
## <a name="example"></a>例  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボード アニメーション間で HandoffBehavior を指定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
