---
title: "方法 : タイムラインを自動的に反転するかどうかを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2abce54905f0bb06bf983c065e064ce2dfeba932
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>方法 : タイムラインを自動的に反転するかどうかを指定する
タイムラインの<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティは、順方向の反復の完了後に逆方向に再生するかどうかを決定します。 次の例では、同じ期間とターゲットの値ではなく、異なるいくつかのアニメーション<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定します。 示すためにどのように<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティが異なる動作<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>を繰り返す設定、いくつかのアニメーションが設定されています。 最後のアニメーション表示方法、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティの入れ子になったタイムラインで動作します。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
